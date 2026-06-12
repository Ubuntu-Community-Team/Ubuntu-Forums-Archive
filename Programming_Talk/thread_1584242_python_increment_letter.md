---
title: "python increment letter"
date: 2010-09-28
forum: Programming Talk
---

### Post by rajan on 2010-09-28
hi, real quick question:
how can i increment the letter in a string in python?

i have to write something of the sort:
```

HETATM    1  CAA TTHP    0       0.000   0.000   0.000  0.00  1.00            C
HETATM    2  CAB TTHP    0       0.326   0.774   2.490  0.00  0.00            C
HETATM    3  CAC TTHP    0      -0.761  -1.076  -1.706  0.00  0.00            C
HETATM    4  CAD TTHP    0      -1.247  -0.178  -2.106  0.00  0.00            C
HETATM    5  CAE TTHP    0      -0.656  -0.409   2.289  0.00  0.00            C
HETATM    6  CAF TTHP    0      -0.831  -0.336   2.379  0.00  0.00            C
HETATM    7  CAG TTHP    0       1.249  -1.237  -2.319  0.00  0.00            C
HETATM    8  CAH TTHP    0      -1.058  -0.847  -0.064  0.00  0.00            C
HETATM    9  CAI TTHP    0      -0.733  -1.075   2.496  0.00  0.00            C
HETATM   10  CAJ TTHP    0       0.031   0.448  -0.669  0.00  0.00            C
```

but i don't want to increment the letters "CAA" to "CAJ" by hand (as was done in this case). i assume there is some library that i could import, but i don't know which one. i'm a beginner in python so i apologize for the dumb question -- i've googled a bit and nothing substantial.

---

### Post by Bachstelze on 2010-09-28
You could do it yourself.  Subclassing the string class and overloading the + operator to "increment" the string would probably teach you a lot of nice things about Python. ;)

And no, I don't know a library that does that either.

---

### Post by mo.reina on 2010-09-29
the quick and dirty way


```
>>> letters = ['A', 'B', 'C', 'D']
>>> for x in range(4):
...   print('CA{}'.format(letters[x]))
... 
CAA
CAB
CAC
CAD
```

of course, if you want it to increment beyond 'Z', say:
CAZ
CBA
CBB
CBC

then you'll have to modify things a bit, but basically the premise is that since the letters are placed in an array, and the array elements are accessible by indexing, as long as the lettersa are placed in alphabetical order it will work as advertised.

by the way, those look like some sort of protein/amino acid combinations... is this some sort of biogenetics program?

---

### Post by spjackson on 2010-09-29
Or this
```

for n in range(10):
    str = "CA" + chr(ord('A') + n)
    print n+1, str

```

---

### Post by mo.reina on 2010-09-29
> **Bachstelze said:**
> You could do it yourself.  Subclassing the string class and overloading the + operator to "increment" the string would probably teach you a lot of nice things about Python. ;)

And no, I don't know a library that does that either.

i'd actually like to see an example of this, without using the ord function to generate the ascii values.  

i took a look at the objectstring.c, which i think is the source for the string class, but being written in c i couldn't understand any of it.  of course you don't need to take a look at the string source to subclass it, but i thought it would be useful to see how it could be done.

---

### Post by Bachstelze on 2010-09-29
Of course you still need to use ord and chr, but overloading the + operator makes it more convenient, and more Pythonic.

```
firas@aoba ~ % cat mystring.py
class MyString(str):
    def __add__(self, x):
        # If we're trying to add anything but an int, do normal string
        # addition.
        if type(x) is not int:
            return str.__add__(self, x)

        res = ''
        i = len(self)-1
        while x > 0:
            # Get the ASCII code of the i-th letter and "normalize" it
            # so that a is 0, b is 1, etc.
            # If we are at the end of the string, make it -1, so that if we
            # need to "add" 1, we get a.
            if i >= 0:
                c = ord(self[i]) - 97
            else:
                c = -1

            # Calculate the number of positions by which the letter is to be
            # "rotated".
            pos = x % 26

            # Calculate x for the next letter, add a "carry" if needed.
            x //= 26
            if c + pos >= 26:
                x += 1

            # Do the "rotation".
            c = (c + pos) % 26

            # Add the letter at the beginning of the string.
            res = chr(c + 97) + res

            i -= 1

        # If we didn't reach the end of the string, add the rest of the string back.
        if i >= 0:
            res = self[:i+1] + res

        return MyString(res)


```

You create a MyString like this:

```
firas@aoba ~ % python3
Python 3.1.2 (r312:79147, Jul  4 2010, 04:41:31) 
[GCC 4.2.1 (Apple Inc. build 5659)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> from mystring import *
>>> s = MyString('abcdefg')
```

It's like a normal string, you can print it, concatenate it and do all the normal string methods:

```
>>> s
'abcdefg'
>>> print(s)
abcdefg
>>> s + 'foo'
'abcdefgfoo'
>>> s.find('f')
5
>>> s.split('f')
['abcde', 'g']

```

Except when you try to add an int:

```
>>> for i in range(27): print(s+i)
... 
abcdefg
abcdefh
abcdefi
abcdefj
abcdefk
abcdefl
abcdefm
abcdefn
abcdefo
abcdefp
abcdefq
abcdefr
abcdefs
abcdeft
abcdefu
abcdefv
abcdefw
abcdefx
abcdefy
abcdefz
abcdega
abcdegb
abcdegc
abcdegd
abcdege
abcdegf
abcdegg
>>> for i in range(15): print(s + (26**i))
... 
abcdefh
abcdegg
abcdffg
abceefg
abddefg
accdefg
bbcdefg
aabcdefg
azabcdefg
azzabcdefg
azzzabcdefg
azzzzabcdefg
azzzzzabcdefg
azzzzzzabcdefg
azzzzzzzabcdefg
>>> s + 10**150
'aztftdaiomsungceenakskjgavxsrlebufijstgntuyznnmvucsjivupttukyeiplcntaqziulothfvxztahklwlckhidcbquwtxvrxucku'

```

Does not work with substraction (though it would be easy to add it, I'll leave it as an exercise to the reader)

```
>>> s - 1
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unsupported operand type(s) for -: 'MyString' and 'int'
```

But the code needs to be changed for handling negative numbers:

```
>>> s + (-1)
'zabcdef'

```

---

### Post by rajan on 2010-09-29
lots of great ideas! thanks a lot. part of the reason for posting was to make sure that i wasn't missing something really simple. 

@ mo.reina, it is a NAMD simulation that I'm trying to make the input for via a python script. basically, i am creating a pdb file (usually used for protein structures) to specify the locations of particles for a minimization of the potential energy. the entire python script is below and the purpose of it is to make charged particles on the surface of a sphere and so that they distribute themselves evenly around it. this is one of the problems that hasn't been solved analytically and thus needs a numeric solution, such as the one NAMD provides. 


```
import sys
import math
import numpy
import random

RandPts  = sys.argv[1] # File to place random points into
ConfFile = sys.argv[2] # Config file to write
PSFfile  = sys.argv[3] # PSF to write

f = open(RandPts,"w")
g = open(ConfFile,"w")

li = 0

numpts = int(raw_input('How Many Points?   '))

outputName = 'SphDistOut'+str(numpts)+'.pdb'
paramFile  = 'SphDistrNAMD.prm'
FixPts     = 'SphDistrFix.pdb'

x = []
y = []
z = []

r = 2.5
Welldepth = 500.00

#################################################################
### PDB file written, containing fixed atom at origin         ###
#################################################################

# 1.00 in beta column of line below informs namd to regard CAA as fixed

f.write('HETATM    1  CAA TTHP    0       0.000   0.000   0.000  0.00  1.00            C\n')

for li in range(0,numpts):
    incr = 2 * math.pi / numpts
    
    xhld = random.random() * 2 * math.pi
    x.append(r * math.sin(xhld) * math.cos(xhld))
    yhld = random.random() * 2 * math.pi
    y.append(r * math.sin(yhld) * math.cos(yhld))
    zhld = random.random() * 2 * math.pi
    z.append(r * math.cos(zhld))

    f.write('HETATM  %3d  CAA TTHP    0      %- 2.3f  %- 2.3f  %- 2.3f  0.00  0.00            C\n' % (li+2, x[li], y[li], z[li]))

    li = li + 1

# you will need to replace the "CAA" with unique id for each atom


f.close()

#################################################################
# Write conf file for minimization, bare minimum params given ###
#################################################################

g.write('############################################################# \n')
g.write('####       Conf File Generated by SphereDist.py         ##### \n')
g.write('############################################################# \n')
g.write('####       Input Files Below                            ##### \n \n')
g.write('structure          %s \n' % PSFfile)
g.write('coordinates        %s \n' % RandPts)
g.write('outputName         %s \n \n' % outputName)
g.write('temperature         0 \n')
g.write('############################################################# \n')
g.write('####         Simulation Parameters                      ##### \n')
g.write('############################################################# \n \n')
g.write('paraTypeCharmm         on \n')
g.write('parameters          %s \n\n\n' % paramFile)
g.write('fixedAtoms          on \n')
# fixedAtomsCol       B tells namd to look in the beta column of pdb for 
# fixed atoms mentioned in fixedAtoms          on line
g.write('fixedAtomsCol       B \n\n')
g.write('# Force-Field Parameters \n\n')
# must exclude none from calc, or electrostatic E will = 0
g.write('exclude             none \n')
g.write('1-4scaling          1.0 \n')
g.write('cutoff              99 \n')
g.write('switching           off \n')
g.write('pairlistdist        100 \n')
# binaryoutput = no will print minimized points to <outputname>.pdb.coor
g.write('binaryoutput        no \n\n')
g.write('############################################################# \n')
g.write('####         Execution Script                           ##### \n')
g.write('############################################################# \n \n')
# change number below to make simulation shorter or longer as needed
g.write('minimize            10000 \n')
g.write('run 0 \n')

g.close()

#################################################################
#### Write psf file                                         #####
#################################################################

numptplone = numpts + 1

i = open(PSFfile,"w")
i.write('PSF\n\n         3 !NTITLE\n')
i.write(' REMARKS PSF generated by SphDistrNAMD.py\n')
i.write(' REMARKS topology no_topology_file\n')
i.write(' REMARKS segment TTH { first NONE; last NONE; auto none  }\n')
i.write('\n')
i.write('       %3d !NATOM \n' % numptplone)

typ    = 'CG999'
# mass/charge are not related to anything physical
charge = 3.000000
mass   = 15.9994
li = 1

i.write('       1 TTH  0    TTHP CAA  CG000   3.000000        15.9994           C\n')

# again, you will have to change the "CAA" to a unique id

for li in range(1,numpts+1):
    i.write('       %3d TTH  0    TTHP CAA  %s  % 1.6f       % 2.4f           C\n' % (li + 1, typ, charge, mass))
    li = li + 1

li    = 1
lincr = 0
dummy = 1

# bonds are problematic. cut the appropriate bonds out of the psf

i.write('\n')
i.write('       %3d !NBOND: bonds\n' % numpts)
for li in range(1,numpts+1):
    i.write('       1       %3d       1       %3d       1       %3d       1       %3d\n' % (dummy + 1 + (lincr*4), dummy + 2 + (lincr*4), dummy + 3 + (lincr*4), dummy + 4 + lincr*4))
    lincr = lincr + 1



i.write('\n')
i.write('       0 !NTHETA: angles \n')
i.write('\n\n')
i.write('       0 !NPHI: dihedrals \n')
i.write('\n\n')
i.write('       0 !NIMPHI: impropers \n')
i.write('\n\n\n')
i.write('       0 !NDON: donors \n')
i.write('\n\n')
i.write('       0 !NACC: acceptors \n')
i.write('\n\n')
i.write('       0 !NNB \n \n')

i.close()


#################################################################
#####  Write Param File                                     #####
#################################################################

ParF = open(paramFile, "w")

ParF.write('*Nothing even close to CHarmM here, just a bunch of fake params << \n')
ParF.write('*>>>>> for the purpose of making the simulation as real   <<<<<<< \n')
ParF.write('*>>>>>>>>>>>>>>>>>>>>>>  as possible   <<<<<<<<<<<<<<<<<<<<<<<<<< \n')
ParF.write('\n\n\n')
ParF.write('BONDS \n')
ParF.write('CG000  CG999  % 3.2f     % 1.4f ! from SphDistrNAMD.py \n' % (Welldepth,r))
ParF.write('\n \n \n')
ParF.write('NONBONDED nbxmod  5 atom cdiel shift vatom vdistance vswitch - \n')
ParF.write('cutnb 14.0 ctofnb 12.0 ctonnb 10.0 eps 1.0 e14fac 1.0 wmin 1.5 \n')
ParF.write('                !adm jr., 5/08/91, suggested cutoff scheme \n')
ParF.write('!see mass list above for better description of atom types \n')
ParF.write('!hydrogens \n')
# if these parameters below are used in simulation, something's wrong
ParF.write('CG999     0.0       -0.0450     1.3400 !  \n')
ParF.write('CG000     0.0       -0.0350     1.3400 !  \n')
ParF.write('\n \n \n')
ParF.write('END \n')

ParF.close()
```

---

### Post by mo.reina on 2010-09-29
> **Bachstelze said:**
> Of course you still need to use ord and chr, but overloading the + operator makes it more convenient, and more Pythonic.

```
firas@aoba ~ % cat mystring.py
class MyString(str):
    def __add__(self, x):
        # If we're trying to add anything but an int, do normal string
        # addition.
        if type(x) is not int:
            return str.__add__(self, x)

        res = ''
        for i in range(1, len(self)+1):
            # Get the ASCII code of the i-th letter (starting from the right
            # of the string) and "normalize" it so that a is 0, b is 1, etc.
            c = ord(self[-i]) - 97

            # Calculate the number of positions by which the letter is to be
            # "rotated".
            pos = x // (26**(i-1))

            # Do the "rotation".
            c = (c + pos) % 26

            # Add the letter at the beginning of the string.
            res = chr(c + 97) + res

        return res

```



The rotation trick is quite nice, I was trying to figure out how to rotate the letters after 26

My own implementation (not as neat as yours)

```
class MyClass:
    def __init__(self, name):
        self.name = name
    def __add__(self, other):
        for x in range(1, len(self.name)):
            a = list(self.name)[-1 * x]
            return self.name[:len(self.name)-x] + chr(ord(a) + other)
```


```
>>> from test import MyClass
>>> CAA = MyClass('CAA')
>>> CAA + 1
'CAB'
>>> CAA + 2
'CAC'
>>> CAA + 15
'CAP'
```

---

### Post by Bachstelze on 2010-09-29
Note: I updated the code above. It failed in some corner cases. (also it returned a regular string, not a MyString)

---

### Post by Bachstelze on 2010-09-29
> **mo.reina said:**
> The rotation trick is quite nice, I was trying to figure out how to rotate the letters after 26


It's basically the same algorithm you use since second grade when you add numbers. ;) The only difference is that you "roll over" when you reach 26, not 10.

---

### Post by schauerlich on 2010-09-29
python's int uses any base from 2-36, you could use base 36 and shift by 10.

---

### Post by Bachstelze on 2010-09-29
> **schauerlich said:**
> python's int uses any base from 2-36, you could use base 36 and shift by 10.

Or treat the string as a base 26 int, and just do arithmetic addition, then convert the result back.

The problem will be what happens when you have for example 'z' and want to add 1. It will convert to 10 in base 26, which will translate to 'ba'. Probably not what you want.

(Hence why I set c to -1 when the end of the string is reached, not to 0.)

---

### Post by ssam on 2010-09-30
itertools has what you need.

```

import itertools

["".join(x) for x in itertools.product("abc", repeat=3)]

```

---

### Post by rajan on 2010-09-30
excellent! here's what i have:

```

names = ["".join(xABC) for xABC in itertools.product("ABCDEFGHIJKLMNOPQRSTUVWXYZ", repeat=2)]

for li in range(0,numpts):
    
    # assign random cartesian points to arrays x, y, and z
    xhld = random.random() * 2 * math.pi
    x.append(r * math.sin(xhld) * math.cos(xhld))
    yhld = random.random() * 2 * math.pi
    y.append(r * math.sin(yhld) * math.cos(yhld))
    zhld = random.random() * 2 * math.pi
    z.append(r * math.cos(zhld))

    f.write('HETATM  %3d  C%s TTHP    0      %- 2.3f  %- 2.3f  %- 2.3f  0.00  0.00            C\n' % (li+2, names[li+1], x[li], y[li], z[li]))

    li = li + 1

```

it iterates through the alphabet, and the product function is exactly what i need since it increments from right to left. this works up to 99 iterations and probably past that, but i only tested up to 99. 

i really appreciate all the ideas and it definitely has taught me a lot of python.

---

