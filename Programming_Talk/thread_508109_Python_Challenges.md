---
title: "Python Challenges"
date: 2007-07-23
forum: Programming Talk
---

### Post by Nekiruhs on 2007-07-23
Heres an Idea!
Why not post some challenges here, with a rating on a scale of five. That other people can answer in Python (Or other languages). That way, we all learn, and generate useful scripts/programs.

Heres one:

Difficulty: *
Challenge: Write a script to figure out an algebraic equations in the form of x + y * A = B and x / A  - y = B. Where x and y are variables and A and B are known. Should ask for input on A and B. Solve for X.

---

### Post by kevinlyfellow on 2007-07-23
Actually, there is a great website that posses these questions.  [http://www.projecteuler.net/](http://www.projecteuler.net/)

What exactly is it that you want in your challenge?  One can't come up with a single solution to the question you have posed since there is only one equation and two unknowns.  Are you looking for a solution in terms of a particular variable?

---

### Post by Peyton on 2007-07-23
Right, there are going to be infinitely many solutions.

---

### Post by Nekiruhs on 2007-07-23
Whoops. Forgetting my basic algebra, stupid me. Its fixed now.. Yes, it should get input from the user on what A and B are, then solve for x (*cough* substitution *cough*).

---

### Post by pmasiar on 2007-07-24
hmmm, python challenges... like [http://www.pythonchallenge.com/](http://www.pythonchallenge.com/) ? :-D

---

### Post by Nekiruhs on 2007-07-24
> **pmasiar said:**
> hmmm, python challenges... like [http://www.pythonchallenge.com/](http://www.pythonchallenge.com/) ? :-D

That site confuses me, I solved the first one, got it right, now how do I go to the next one?

---

### Post by pmasiar on 2007-07-24
solution is URL (pagename) for the next one no? 

And BTW it havs forums (per level) where you can ask questions (and most of them already answered).

Enjoy!

---

### Post by smartbei on 2007-07-24
That is a cute challenge, though I wouldn't give it three stars - it is very simple. Here is the answer code I came up with:
```

while 1:
	x=raw_input("Please input values in the format x,x=A,B: ")
	if x=="exit": break
	l=x.split(",")
	A,B=int(l[0]),int(l[1])
	y=(B/A-B)/2
	x=B-y*A
	print "X=",x
	print "Y=",y

```
Here is another of the same vein (and somewhat more useful):

**Difficulty:** **
**Challenge:** Write a program that solves quadratic equations of the form: Ax^2+Bx+C=0 for x given A, B and C. Should ask for input for A, B and C and print out answer.

---

### Post by Nekiruhs on 2007-07-24
I solved it, heres my script:

```
#!/usr/bin/env python

import os
import sys
import math

valInput = raw_input("Enter A,B,C values seperated by commas: ")
values = valInput.split(",")

A = values[0]
B = values[1]
C = values[2]


x1 = -int(B) + ((math.sqrt((int(B)^2)) - 4 * int(A) * int(C)))
x2 = -int(B) - ((math.sqrt((int(B)^2)) - 4 * int(A) * int(C)))

if x1 is x2:
    print("X = " + x1)
else:
        print("X = " + str(x1) + " and " + str(x2))	
	
```
I didn't know about the split function of a string until i saw yours. I'll think of a challenge later, please keep posting them in the mean time.  BTW, I really like Geany, i just saw you post in the IDE thread, its great.

---

### Post by Nekiruhs on 2007-07-25
Ok, new challenge:
Difficulty: **
Write a script to ask the user for input on Full name, Last Name, and Age. Allow the user to do this multiple times. At the end of execution, write the info gathered into a file named Info.txt in the users home directory.

---

### Post by smartbei on 2007-07-25
Your previous solution to the quadratic solver I proposed is incorrect. Given the input 1,2,1 it gives out X=-6,2. The correct answer is X=-1.

Here is the problem:
```

x1 = -int(B) + ((math.sqrt((int(B)^2)) - 4 * int(A) * int(C)))
x2 = -int(B) - ((math.sqrt((int(B)^2)) - 4 * int(A) * int(C)))

```
should be changed to:
```

#this is just to save typing...might as well convert to int here:
A = int(values[0])
B = int(values[1])
C = int(values[2])

#note the change in the parenthases and the use of ** - that is the python power function. ^ is a bitwise xor.
x1 =(-B + math.sqrt(B**2 - 4 * A * C))/2.0
x2 =(-B - math.sqrt(B**2 - 4 * A * C))/2.0

```

Also, 'is' is not the correct way to compare numbers - use ==. Finally, a simpler way to use print statements (with which you dont need to convert to string) is:
```

if x1==x2:
	print "X =",x1
else:
	print "X =",x1,"and",x2

```
See that it replaces every comma with a space when it prints out in a terminal.

---

### Post by Nekiruhs on 2007-07-25
Ok, I see what you mean now. I could have sworn that i read that ^ worked in Python, w/e lol.  I knew there had to be a better way to do the int converison. Also thanks for pointing out the is vs == thing.

---

### Post by smartbei on 2007-07-25
In answer to your challenge:
```

x=raw_input("how many people would you like to store? ")
x=int(x)
if x < 1:
	raise "X is too small"
print "Now you will be prompted for information about these people."
l=[]
questions=('first name','last name','age')

for a in range(1,x+1):
	ll=[]
	print "Person "+str(a)+":"
	for b in questions:
		r=raw_input("What is person #"+str(a)+"'s "+b+"? ")
		ll.append(r)
	l.append(ll)

r=raw_input("Do you want to write this data to your home directory?[y/n] ")
if r=="y":
	r=raw_input("Please enter a name for this file, which will be placed in the home directory: ")
	from os.path import expanduser
	f=open(expanduser("~/")+r,"w")
	for a in l:
		f.write(a[0]+","+a[1]+","+a[2])
	f.close()
print "Succesfully written data"

```

Now for the next challenge:
**Difficulty:** ***
**Challenge:** Write a program that reads the data output by the previous challenge into a file and lets the user search for a particular person by first name.  Assume that all first names are different, how efficient can this be made? (Hint - think binary search) Were are looking for efficiency as in lookup time, not memory.

---

### Post by Nekiruhs on 2007-07-25
Clever challenge. I'll set to work on it immediatly. I have learned a lot already just by these challeneges, this is a great way to learn a language

---

