---
title: "need a language for a simple task"
date: 2009-05-21
forum: Programming Talk
---

### Post by rajan on 2009-05-21
Hi,
 I have a xy array that is about 300 lines long and i want to multiply each y value by another y value from another xy array. For example, i have the array:

1 3
2 2
3 3
4 2
...

and i want to multiply the y coordinate by another array's y value. The second array may look something like this:

0.5 2
1 2
1.5 4
2 30
2.5 7
3 8
...

I have tried the linear convolution on xmgrace, but that gave me strange numbers, and I am not sure at all how to use it (the user's manual simply says "performs a linear convolution of 2 sets"). 

I am looking for some advice on which program I should use. I understand I'll probably have to learn it, but I'm reasonably familiar with most languages out there. Specifically, I've seen examples on the internets that use perl and python. Both would be good. 

Any advice is appreciated.

---

### Post by Zugzwang on 2009-05-21
For numerical mathematics, "octave" is a reasonable choice. Here's a snipplet from an interactive session:

```

octave:1> A = [1 3; 2 2; 3 3; 4 2]
A =                               

   1   3
   2   2
   3   3
   4   2

octave:2> B = [0.5 2; 1 2; 1.5 4; 2 30]
B =                                    

    0.50000    2.00000
    1.00000    2.00000
    1.50000    4.00000
    2.00000   30.00000

octave:3> A(:,2) = A(:,2).*B(:,2)
A =

    1    6
    2    4
    3   12
    4   60

```

In the last command, "A(:,2)" means: "take every row of A and the second column". Furthermore, ".*" means "element-wise multiplication".

It's in the repositories and basically allows you to twiggle around with matrices and other mathematical concepts. All basic algorithms are implemented already. It's a more-or-less clone of "MATLAB" which is very popular among engineers and scientists (like economics people) that just want to apply their stuff without learning much programming.

---

### Post by sujoy on 2009-05-21
in python:

say there is a tuple (x,y) containing the co-ordinates.
now get two list for the two arrays of co-ordinates
list1[(x1,y1),(x2,y2)....]
list2[(q1,w1),(q2,w2)....]

```

#!/usr/bin/env python

list1=[(1,3),(2,2),(3,3),(4,2)]
list2=[(0.5,2),(1,2),(1.5,4),(2,30)]

list3=[list1[i][1]*list2[i][1] for i in range(len(list1))]
list3=zip([x for (x,y) in list1],list3)

print list3
```

---

### Post by rajan on 2009-05-21
thanks for the quick replies! i completely forgot about mathematica... i am going to try that. thanks for reminding me, Zugzwang. 

sujoy, do you suggest python or perl for something like this?

to specify my problem further, i am looking at fluorescence data that gives me a certain numerical value for the intensity at a specific wavelength. thus, i have a file of xy data, the x being the wavelength (300 to 850 usually), and the y being the intensity. I need to multiply the intensities by a scaling factor that is wavelength dependent. thus i have another file of xy data with almost identical formatting, but different y values (and some of the x values are different). 

mathematica seems to be reasonably good with this, but the different x values might cause a problem. for this reason, i'm interested in moving to perl/python/octave if mathematica cannot handle it.

---

### Post by sujoy on 2009-05-21
i am not experienced in octave, but both perl and python will let you do that easily.

in fact the above code snippet works as long as both the list are of equal length, otherwise, it just leaves the extra elements in the second list (that'd be the wavelength one), and is operational irrespective of x being same in both the lists.

it seems, you'r actuall problem would be to create the lists from the two files. whether the two lists needs to be correspond based on the x ordinate value, etc. once that is determined, a quick sed or awk can turn in into a list usable by python and carry on from there.

perl too is a viable alternative here. infact almost any language that can deal with lists will do.

---

### Post by imdano on 2009-05-21
> **sujoy said:**
> ```

#!/usr/bin/env python

list1=[(1,3),(2,2),(3,3),(4,2)]
list2=[(0.5,2),(1,2),(1.5,4),(2,30)]

list3=[list1[i][1]*list2[i][1] for i in range(len(list1))]
list3=zip([x for (x,y) in list1],list3)

print list3
```

I think you can simplify this a bit:
```
#!/usr/bin/env python

list1 = [(1,3), (2,2), (3,3), (4,2)]
list2 = [(0.5,2), (1,2), (1.5,4), (2,30)]
list3 = [(x[0], x[1] * y[1]) for x, y in zip(list1, list2)]
```

---

### Post by sujoy on 2009-05-21
nice, yea thats a lot more simple :)

---

### Post by ibuclaw on 2009-05-21
Haskell's list comprehension is good at this too:

```
zipWith (zipWith (*)) [[1,3],[2,2],[3,3],[4,2]] [[0.5,2],[1,2],[1.5,4],[2,30]]
```

But still, not as readable as octave.

Regards
Iain

---

### Post by WW on 2009-05-21
Based on your description of the problem, it appears to me that none of the solutions presented so far are correct.  They all assume that the x coordinate of the corresponding points in the two lists are the same, but even in your example data, they are not.

Do you know if all the x coordinates of the data in the first list are also in the second list somewhere?  If so, then (speaking in python terms) you can create a dictionary from the second list to find the corresponding scaling factor for the y values in the first list.  Otherwise, you will have to [interpolate](http://en.wikipedia.org/wiki/Interpolation).

---

### Post by fr4nko on 2009-05-21
Just for fun, the equivalent ocaml expression:

```
let mymul m1 m2 =
  let ir = 
    let f ls (x, y) (x', y') = (x, y *. y') :: ls in
      List.fold_left2 f [] m1 m2 in
    List.rev ir
;;

let result =
  let m1 = [(1.0 ,3.0); (2.0, 2.0); (3.,3.); (4.,2.)]
  and m2 = [(5., 2.); (1., 2.); (1.5, 4.); (2., 30.)] in
    mymul m1 m2;;

List.iter (fun (x, y) -> Printf.printf "(%g, %g)\n" x y) result ;;

```Please note that it is longer than Haskell code because in Haskell all the real work is done by zipWith. I've also included the code to print the result.

ocaml rules but I don't mean it is a practical solution for your problem ;-)

Francesco

---

### Post by rajan on 2009-05-21
yeah i figured i would have to interpolate. 

another problem is that the x coordinates do not start at the same place every time. for example, the x coordinate for a few files are 360 nm (without the "nm"), 380, 510, 610, and the file containing the multipliers starts at 375. I was thinking of ways to make sure i am actually multiplying the 380nm factor with the 380nm intensity (due to the mismatched starting positions). I was thinking that i might have to minimize the difference with a simple subtraction routine. is there a built-in function for this? 

i'm glad python was suggested -- i've always wanted to learn it. 

thanks for the help,
rajan

---

### Post by gtr32 on 2009-05-21
I don't think the language is so important here, it should be simple in most of them. I think I have what you're looking for in C++ code. It's a piece that takes in a frequency and looks up a path loss on cable path for that frequency. That specific frequency is not necessary part of the calibration data so it might need to be calculated (linear or logarithmic interpolation).

---

### Post by rajan on 2009-05-22
well, i think i have a reasonable facsimile of a python code that can do what i wanted. 


I'm posting the code and hopefully this helps someone else and maybe someone can point out some of the egregious errors i'm making.

```

# start by asking user for filename and opening file

namef=raw_input("Filename for sensitivity data?")
f=open(namef,"r")

sensitivity = [[],[]]

lineint = 0

# read spectral sensitivity file into the 2xn sensitivity array

for line in f.readlines():

	string1 = line
	x1,y1 = [float(x) for x in string1.split( )]
	sensitivity[0].append(x1)
	sensitivity[1].append(y1)
	lineint = lineint + 1

datafile = [[],[]]

# ask user for data file, open file

namegf=raw_input("Filename for data file?")
g=open(namegf,"r")

lineint1 = 0

# read in data file to 2xn datafile array

for liner in g.readlines():

	string1 = liner
	x1,y1 = [float(x) for x in string1.split( )]
	datafile[0].append(x1)
	datafile[1].append(y1)
	lineint1 = lineint1 + 1

g.close()
f.close()

# print fctn confirmed lineint1 = total amount of lines in data file

# print fctn confirmed datafile and sensitivity arrays contain correct data

# test for data file's starting point and interpolate between closest 2 values

counter1 = 0
counter2 = 0
newarray = [[],[]]

# print fctn confirmed array elements are multiplicable

while datafile[0][0]-sensitivity[0][counter1] > .29:
	counter1 += 1

# calculate new intensity for first point
newintensity = (1-(abs(datafile[0][0] - sensitivity[0][counter1])/abs(sensitivity[0][counter1] - sensitivity[0][counter1+1]))) * sensitivity[1][counter1] * datafile[1][0] + (1-(abs(datafile[0][0] - sensitivity[0][counter1+1])/abs(sensitivity[0][counter1] - sensitivity[0][counter1+1]))) * sensitivity[1][counter1+1]* datafile[1][0]
newarray[0].append(datafile[0][0])
newarray[1].append(newintensity)

# ask user for new data file, open file in write mode

namehf=raw_input("Filename for new data file?")
h=open(namehf,"w")

fileline1 = str(newarray[0][0])
fileline2 = str(newarray[1][0])
fileline3 = "\n"
fileline = fileline1
fileline += "  "
fileline += fileline2
fileline += "  "
fileline += fileline3
fileline = "".join(fileline)
h.write(fileline)

# continue on to rest of points

# counter3 keeps track of lines in the data file, compares to lineint
counter3 = 0

while counter1 < lineint:
	counter2 += 1
	# increase counter2 to flip through all the data file's x coords
	while abs(datafile[0][counter2]-sensitivity[0][counter1]) > .29:
		counter1 += 1
		if counter1 >= lineint: break

	if datafile[0][counter2]-sensitivity[0][counter1] >= 0:
		newintensity = (1-(abs(datafile[0][counter2] - sensitivity[0][counter1])/abs(sensitivity[0][counter1] - sensitivity[0][counter1+1]))) * sensitivity[1][counter1] * datafile[1][counter2] + (1-(abs(datafile[0][counter2] - sensitivity[0][counter1+1])/abs(sensitivity[0][counter1] - sensitivity[0][counter1+1]))) * sensitivity[1][counter1+1] * datafile[1][counter2]
		newarray[0].append(datafile[0][counter2])
		newarray[1].append(newintensity)
		counter3 += 1

	elif datafile[0][counter2]-sensitivity[0][counter1] < 0:
		newintensity =  (1-(abs(datafile[0][counter2] - sensitivity[0][counter1])/abs(sensitivity[0][counter1] - sensitivity[0][counter1-1]))) * sensitivity[1][counter1] * datafile[1][counter2] + (1-(abs(datafile[0][counter2] - sensitivity[0][counter1-1])/abs(sensitivity[0][counter1] - sensitivity[0][counter1-1]))) * sensitivity[1][counter1-1] * datafile[1][counter2]
		newarray[0].append(datafile[0][counter2])
		newarray[1].append(newintensity)
		counter3 += 1


       	fileline1 = str(newarray[0][counter2])
       	fileline2 = str(newarray[1][counter2])
       	fileline3 = "\n"
       	fileline = fileline1
       	fileline += "  "
       	fileline += fileline2
       	fileline += "  "
       	fileline += fileline3
       	fileline = "".join(fileline)
	h.write(fileline)


h.close()

print "got here"


```

i've never written a python code before so i'm sorry about the poor quality. 

i'm not sure who i'm more scared of right now, my boss because i spent almost all day doing this myself, or my wife because it's 11pm and i'm not home yet. 


thanks again for all the help. it is much appreciated.


EDIT: replaced with code that actually works

---

### Post by rajan on 2009-05-23
I have posted the corrected code in the above posting (as an edit), and it is finally working. I do get an error at the end of the run, though (which is annoying, but I still get the data I want). It is from the ```
while counter1 < lineint:
	counter2 += 1
	# increase counter2 to flip through all the data file's x coords
	while abs(datafile[0][counter2]-sensitivity[0][counter1]) > .29:
		counter1 += 1
		if counter1 >= lineint: break
```

because counter1 keeps iterating past the end of the sensitivity[0][counter1] limits. The actual error is posted here:

```
Traceback (most recent call last):
  File "scaling.py", line 91, in ?
    newintensity = (1-(abs(datafile[0][counter2] - sensitivity[0][counter1])/abs(sensitivity[0][counter1] - sensitivity[0][counter1+1]))) * sensitivity[1][counter1] * datafile[1][counter2] + (1-(abs(datafile[0][counter2] - sensitivity[0][counter1+1])/abs(sensitivity[0][counter1] - sensitivity[0][counter1+1]))) * sensitivity[1][counter1+1] * datafile[1][counter2]
IndexError: list index out of range

```

you can see that I tried to escape the nested while loop with the line
```
		if counter1 >= lineint: break
```
but that only breaks out of the if statement. Is there any way to get out of the parent loop? 

thanks again,

rajan

---

