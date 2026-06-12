---
title: "[Python] Improve loop"
date: 2009-02-18
forum: Programming Talk
---

### Post by clog on 2009-02-18
Hello,

I'm coming from C and starting to use Python. I'm currently trying to convert one of my C code to Python in the aim to compare the performances. Here is what the program does:
- reading of an atom list (2 species of molecule)
- for each molecule of the first specie, find all the molecules of the second specie within a cut-off distance
That means playing with tables and doing a lot of comparisons (640 molecules of specie 1 and 1350 of specie 2). The problem is that the Python code takes much more time than the C code: less than 1 second for the C without any compilation optimization, about 20 seconds for the Python. As I will have to run the program with much larger files (about 4000 times larger), improving the speed of the Python code is important.
After some tests, it appears that it's the function that finds neighbors (Find_Neighbors) that takes the longest time. Here is the code:
```
#!/usr/bin/env python

import string
import os
from math import radians
from numpy import *

OPT=1

class SimulationBox(object):
	def __init__(self, a=0, b=0, c=0, alpha=0, beta=0, gamma=0):
		self.a = a
		self.b = b
		self.c = c
		
		self.alpha_deg = alpha
		self.beta_deg = beta
		self.gamma_deg = gamma
		self.alpha_rad = alpha
		self.beta_rad = beta
		self.gamma_rad = gamma
		
		self.temp_alpha_cos=0.0
		self.temp_beta_sin=0.0
		self.temp_beta_cos=0.0
		self.temp_gamma_sin=0.0
		self.temp_gamma_cos=0.0
		self.temp_beta_term=0.0
		self.temp_gamma_term=0.0

	def __str__(self):
		return 'a=%f; b=%f; c=%f;\nalpha (deg)=%f; beta (deg)=%f; gamma (deg)=%f;\nalpha (rad)=%f; beta (rad)=%f; gamma (rad)=%f\n'\
		% (self.a, self.b, self.c, self.alpha_deg, self.beta_deg, self.gamma_deg, self.alpha_rad, self.beta_rad, self.gamma_rad)

	def DegtoRad(self):
		self.alpha_rad = radians(self.alpha_deg)
		self.beta_rad = radians(self.beta_deg)
		self.gamma_rad = radians(self.gamma_deg)
		
	def Parameters_For_Orthogonalization(self):
		if self.alpha_deg==90.0 and self.beta_deg==90.0 and self.gamma_deg==90.0:
			self.temp_alpha_cos=0.0
			self.temp_beta_sin=1.0
			self.temp_beta_cos=0.0
			self.temp_gamma_sin=1.0
			self.temp_gamma_cos=0.0
			self.temp_beta_term=0.0
			self.temp_gamma_term=1.0

		elif self.alpha_deg==90.0 and self.gamma_deg==90.0:
			self.temp_alpha_cos=0.0
			self.temp_beta_sin=sin(self.beta_rad)
			self.temp_beta_cos=cos(self.beta_rad)
			self.temp_gamma_sin=1.0
			self.temp_gamma_cos=0.0
			self.temp_beta_term=0.0
			self.temp_gamma_term=self.temp_beta_sin

		else:
			self.temp_alpha_cos=cos(self.alpha_rad)
			self.temp_beta_sin=sin(self.beta_rad)
			self.temp_beta_cos=cos(self.beta_rad)
			self.temp_gamma_sin=sin(self.gamma_rad)
			self.temp_gamma_cos=cos(self.gamma_rad)
			self.temp_beta_term=(self.temp_alpha_cos-self.temp_beta_cos*self.temp_gamma_cos)/self.temp_gamma_sin
			self.temp_gamma_term=sqrt(1.0-pow(self.temp_beta_cos,2)-pow(self.temp_beta_term,2))
			
#		print self.temp_alpha_cos, self.temp_beta_sin, self.temp_beta_cos, self.temp_gamma_sin, self.temp_gamma_cos
#		print self.temp_beta_term, self.temp_gamma_term
		
class Coordinates(object):
	def __init__(self, n_frame=1, n_mol=1, n_atom=1):
		self.n_frame = n_frame
		self.n_mol = n_mol
		self.n_atom = n_atom
		self.symbol = [[["A" for i in range(n_atom)] for j in range(n_mol)] for k in range(n_frame)]
		self.x = zeros((n_frame, n_mol, n_atom))
		self.y = zeros((n_frame, n_mol, n_atom))
		self.z = zeros((n_frame, n_mol, n_atom))
		self.mol_number = zeros((n_frame, n_mol))
		self.atomic_mass = zeros((n_frame, n_mol, n_atom))
		self.CM_x = zeros((n_frame, n_mol))
		self.CM_y = zeros((n_frame, n_mol))
		self.CM_z = zeros((n_frame, n_mol))
	
	def __str__(self):
		tmp = ""
		for i in range(self.n_frame):
			for ii in range(self.n_mol):
				for iii in range(self.n_atom):
					tmp += '%4s %10f %12f %12f %12f\n'\
					% (self.symbol[i][ii][iii], self.atomic_mass[i, ii, iii], self.x[i, ii, iii], self.y[i, ii, iii], self.z[i, ii, iii]) 
		return tmp
		
	def Center_of_Masses(self):
		for i in range(self.n_frame):
			for ii in range(self.n_mol):
				M_TOT = 0.0
				for iii in range(self.n_atom):
					self.CM_x[i,ii] += self.atomic_mass[i, ii, iii] * self.x[i, ii, iii]
					self.CM_y[i,ii] += self.atomic_mass[i, ii, iii] * self.y[i, ii, iii]
					self.CM_z[i,ii] += self.atomic_mass[i, ii, iii] * self.z[i, ii, iii]
					M_TOT += self.atomic_mass[i, ii, iii]
				self.CM_x[i,ii] = self.CM_x[i,ii]/M_TOT
				self.CM_y[i,ii] = self.CM_y[i,ii]/M_TOT
				self.CM_z[i,ii] = self.CM_z[i,ii]/M_TOT
#				print M_TOT, self.CM_x[i,ii], self.CM_y[i,ii], self.CM_z[i,ii]

class Neighbors(object):
	def __init__(self, n_frame=1, n_mol_mol1=1, n_mol_mol2=1):
		self.n_frame = n_frame
		self.n_mol = n_mol_mol1
		self.neighbors = zeros((n_frame, n_mol_mol1, n_mol_mol2))
		self.displ_vec = zeros((n_frame, n_mol_mol1, n_mol_mol2, 3))

def Cartesian_To_Fractional(x, y, z, box):
	frac_coord = zeros(3)
	
	#Pay attention: value of z is used in y!
	z = (z/box.temp_gamma_term) / box.c
	y = ((y-z*box.c*box.temp_beta_term)/box.temp_gamma_sin) / box.b
	x = (x-y*box.b*box.temp_gamma_cos-z*box.c*box.temp_beta_cos) / box.a
	
	frac_coord[0]=x
	frac_coord[1]=y
	frac_coord[2]=z
	
	return frac_coord;

def Fractional_To_Cartesian(x, y, z, box):
	cart_coord = zeros(3)
	
	x = x*box.a + y*box.b*box.temp_gamma_cos + z*box.c*box.temp_beta_cos;
	y = y*box.b*box.temp_gamma_sin + z*box.c*box.temp_beta_term;
	z = z*box.c*box.temp_gamma_term;
	
	cart_coord[0]=x
	cart_coord[1]=y
	cart_coord[2]=z
	
	return cart_coord;

def Find_Neighbors(mol1, mol2, box, mol1_mol2, CutOff=10.0, print_result=0):
	CutOff_square = pow(CutOff, 2)
	Dist_Cart = zeros(3)
	Dist_Frac = zeros(3)
	
	for i in range(mol1.n_frame):
		for ii in range(mol1.n_mol):
			for jj in range(mol2.n_mol):
				Dist_Cart[0] = mol1.CM_x[i,ii] - mol2.CM_x[i,jj]
				Dist_Cart[1] = mol1.CM_y[i,ii] - mol2.CM_y[i,jj]
				Dist_Cart[2] = mol1.CM_z[i,ii] - mol2.CM_z[i,jj]
				
				Dist_Frac = Cartesian_To_Fractional(Dist_Cart[0], Dist_Cart[1], Dist_Cart[2], box)
				for k in range(3):
					if abs(Dist_Frac[k]) > 0.5:
						if Dist_Frac[k] < 0.0:
							Dist_Frac[k] = 1 + Dist_Frac[k]
							mol1_mol2.displ_vec[i,ii,jj,k] = 1.0
						else:
							Dist_Frac[k] = 1 - Dist_Frac[k]
							mol1_mol2.displ_vec[i,ii,jj,k] = -1.0
							
				Dist_Cart = Fractional_To_Cartesian(Dist_Frac[0], Dist_Frac[1], Dist_Frac[2], box)
				
				Dist_Norm_square = pow(Dist_Cart[0],2) + pow(Dist_Cart[1],2) + pow(Dist_Cart[2],2)
				if Dist_Norm_square < CutOff_square and Dist_Norm_square != 0:
					mol1_mol2.neighbors[i, ii, jj] = 1

	if print_result:
		for i in range(mol1.n_frame):
			print "\nFrame %d" % (i)
			for ii in range(mol1.n_mol):
				tmp = 0
				for jj in range(mol2.n_mol):	
					if mol1_mol2.neighbors[i, ii, jj] == 1:
						tmp += 1
				print "Molecule %d: %d Neighbors" % (mol1.mol_number[i, ii], tmp)

			
if __name__ == '__main__':
	box = SimulationBox()
	BEN = Coordinates(1,1350,12)
	PTC = Coordinates(1,640,36)
	print "Creation of coordinates tables done!"
	
	#arrays filling...

	PTC_BEN = Neighbors(PTC.n_frame, PTC.n_mol, BEN.n_mol)
	print "Creation of neighbor tables done!"
	Find_Neighbors(PTC, BEN, box, PTC_BEN, 20.0, 0)
	print "Neighbors found!"

``` 

Do you have any idea of how to improve the speed? I heard about vectorization, but I don't know anything about that...

Thanks in advance

---

### Post by CptPicard on 2009-02-18
Well, a factor of 20 in number-crunching style stuff is not atypical in Python vs. C... there is only so much you can do about that, unfortunately.

---

### Post by Can+~ on 2009-02-18
Could you select a smaller piece of code? The one that slows everything down?

---

### Post by SplinterOfChaos on 2009-02-18
Yes, by posting the smallest, slowest section, the optimizations can be most specific and correct. This is true for all programming.

Ironically, I hear when you really want a fast Python library... you write it in C or C++.

[This essay]("http://www.python.org/doc/essays/list2str.html")  might provide some interesting insights into Python optimizing. 

> from math import radians
from numpy import * I don't know how Python looks up functions, but I might guess you'll get a faster lookup time if you don't use these two lines. If I say math.radians, it's obvious I'm looking for something imported from math; otherwise the interpreter, or your reader for that matter, might have to check if it's a locally defined thing first. (I do know Python checks locals first as hinted to in that article.)

A few of your nested for loops might be able to be broken into "implied loops" (a term from the article), although they'll be incredibly ugly. For example: ```
 for i in [1,2,3,4,5]:
    s += str(i)
```can be written as```
s = "".join([ str(i) for i in [1,2,3,4,5]])
```.

---

### Post by Paul Miller on 2009-02-19
One very easy optimization is to use psyco (if you're using an x86 platform).  All you have to do is add at the top

[php]
import psyco
psyco.full()
[/php]

and you'll gain the benefits of JIT compilation to machine code.

---

### Post by clog on 2009-02-19
Thank you for your advices. Here is the code that slows down the program:
```
	    
    for i in range(mol1.n_frame): # i=1
        for ii in range(mol1.n_mol: #ii goes to 640
            for jj in range(mol2.n_mol): #jj goes to 1330
                Dist_Cart[0] = mol1.CM_x[i,ii] - mol2.CM_x[i,jj]
                Dist_Cart[1] = mol1.CM_y[i,ii] - mol2.CM_y[i,jj]
                Dist_Cart[2] = mol1.CM_z[i,ii] - mol2.CM_z[i,jj]
                
                Dist_Frac = Cartesian_To_Fractional(Dist_Cart[0], Dist_Cart[1], Dist_Cart[2], box)
                for k in range(3):
                    if abs(Dist_Frac[k]) > 0.5:
                        if Dist_Frac[k] < 0.0:
                            Dist_Frac[k] = 1 + Dist_Frac[k]
                            mol1_mol2.displ_vec[i,ii,jj,k] = 1.0
                        else:
                            Dist_Frac[k] = 1 - Dist_Frac[k]
                            mol1_mol2.displ_vec[i,ii,jj,k] = -1.0
                            
                Dist_Cart = Fractional_To_Cartesian(Dist_Frac[0], Dist_Frac[1], Dist_Frac[2], box)
                
                Dist_Norm_square = pow(Dist_Cart[0],2) + pow(Dist_Cart[1],2) + pow(Dist_Cart[2],2)
                if Dist_Norm_square < CutOff_square and Dist_Norm_square != 0:
                    mol1_mol2.neighbors[i, ii, jj] = 1

```
And here are the functions Fractional_To_Cartesian and Cartesian_To_Fractional that are called in each loop:

```
def Cartesian_To_Fractional(x, y, z, box):
	frac_coord = zeros(3) # May be a problem if defined in each loop?
	
	z = (z/box.temp_gamma_term) / box.c
	y = ((y-z*box.c*box.temp_beta_term)/box.temp_gamma_sin) / box.b
	x = (x-y*box.b*box.temp_gamma_cos-z*box.c*box.temp_beta_cos) / box.a
	
	frac_coord[0]=x
	frac_coord[1]=y
	frac_coord[2]=z
	
	return frac_coord

def Fractional_To_Cartesian(x, y, z, box):
	cart_coord = zeros(3) # May be a problem if defined here?
	
	x = x*box.a + y*box.b*box.temp_gamma_cos + z*box.c*box.temp_beta_cos;
	y = y*box.b*box.temp_gamma_sin + z*box.c*box.temp_beta_term;
	z = z*box.c*box.temp_gamma_term;
	
	cart_coord[0]=x
	cart_coord[1]=y
	cart_coord[2]=z
	
	return cart_coord

```

@ SplinterOfChaos: good to know, I'll try to change the code and avoid these from... import...

@ Paul Miller: Thank you for the psyco tip, I'm running some tests

---

### Post by ssam on 2009-02-19
maybe you could use numpy and scipy. they let you shift a loop of calculations into a single array operation (if your code can me refactored in such a way).

---

