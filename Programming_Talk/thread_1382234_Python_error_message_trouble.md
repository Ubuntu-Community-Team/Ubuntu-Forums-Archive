---
title: "Python error message trouble"
date: 2010-01-15
forum: Programming Talk
---

### Post by need more pyton on 2010-01-15
Python 3.1.1

i am working on a small program for personal use which includes this bit here:

m = a*((f*k)-(g*j))    
n = -b*((e*k)-(g*i))   
o = c*((e*j)-(f*i))    

D = m+n+o

whenever i hit this part i get an error message like the one below (I cut out the file name for space and privacy reasons:

Traceback (most recent call last):
  File "   ", line 49, in <module>
    D = m+n+o              #define D
TypeError: Can't convert 'int' object to str implicitly

variables m n and o are all integers and that is the string where I'm declaring D so i think i should assume the data type of whatever I'm assigning it which should be an integer.

if anyone can tell me why python thinks I'm trying to make a sting there and help me fix it I would be very appreciative, thanks.

---

### Post by Tony Flury on 2010-01-15
With an error like this to say positively where the error is we would need the whole of the code - or the minimum code segment that can reproduce the problem.

My guess though would be is that somewhere you assign a string to D - trying doing a 
```

print D

```
just before the line giving an error - and see if D is already defined.

Also try moving the comment - and see if that line works ?

---

### Post by need more pyton on 2010-01-15
I tried moving the "D= m+n+o" line and it had no effect at all the same error occurred and as for a preexisting value for D i put a Print (D) just before the trouble line and i got an error telling me that D had no value and it couldn't be printed.  in short I'm positive D has no value prior to the trouble line and the lines position has little significance.


I've trimmed out most of the stuff that exists for user interface reasons but the functional part of the program is below. I italicized the part that I posted previously (unfortunately the indentation is ruined, but its correct in my source file)


def abort(k):
     kill = ["kill", "kilL", "kiLl", "kiLL", "kIll", "kIlL", "kILl", "kILL", "Kill", "KilL", "KiLl", "KiLL", "KIll", "KIlL", "KILl", "KILL"]
     for form in kill:
          if k == form:
               K = input ("do you want to abort? Y/N")
               if K == "Y":
                    raise SystemExit
     if isinstance(k, str):
          return (k)
     else:
          return (int(k))

                   #compile matrix
print ("Please enter your variable names")
Name_X = abort(input("Variable one: "))
Name_Y = abort(input("Variable two: "))
Name_Z = abort(input("Variable three: "))
a= abort(input("First equation: what is "+Name_X+"'s coeficient?"))
b= int(input("First equation: what is "+Name_Y+"'s coeficient?"))
c= int(input("First equation: what is "+Name_Z+"'s coeficient?"))
d= int(input("First equation: what is the constant?"))
e= int(input("Second equation: what is "+Name_X+"'s coeficient?"))
f= int(input("Second equation: what is "+Name_Y+"'s coeficient?"))
g= int(input("Second equation: what is "+Name_Z+"'s coeficient?"))
h= int(input("Second equation: what is the constant?"))
i= int(input("Third equation: what is "+Name_X+"'s coeficient?"))
j= int(input("Third equation: what is "+Name_Y+"'s coeficient?"))
k= int(input("Third equation: what is "+Name_Z+"'s coeficient?"))
l= int(input("Third equation: what is the constant?"))


[I]m = a*((f*k)-(g*j))    #first minor of D
n = -b*((e*k)-(g*i))   #second minor of D
o = c*((e*j)-(f*i))    #third minor of D
print (D)[/I]

D = m+n+o              #define D
                       #switch to X sub one

m = d*((f*k)-(g*j))    #first minor of X sub one
n = -b*((h*k)-(g*l))   #second minor of X sub one
o = c*((h*j)-(f*l))    #third minor of X sub one
print (m) 
print (n)
print (o)
X_sub_one = m+n+o      #define X sub one
                       #switch to Y sub one

m = a*((h*k)-(g*l))    #first minor of Y sub one
n = -d*((e*k)-(g*i))   #second minor of Y sub one
o = c*((e*l)-(h*i))    #third minor of Y sub one
print (m) 
print (n)
print (o)
Y_sub_one = m+n+o      #define Y sub one
                       #switch to Z sub one

m = a*((f*l)-(h*j))    #first minor of Z sub one
n = -b*((e*l)-(h*i))   #second minor of Z sub one
o = d*((e*j)-(f*i))    #third minor of Z sub one

Z_sub_one = m+n+o      #define Z sub one
                       #Switch to evaluating variables

X= X_sub_one/D         #evaluate X
Y= Y_sub_one/D         #evaluate Y
Z= Z_sub_one/D         #exaluate Z
                       #Begin printing values


print ("Denominator equals: "+str(D))
print (Name_X+" numerator equals: "+str(X_sub_one))
print (Name_Y+" numberator equals: "+str(Y_sub_one))
print (Name_Z+" numberator equals: "+str(Z_sub_one))
print (Name_X+" equals: "+str(X))
print (Name_Y+" equals: "+str(Y))
print (Name_Z+" equals: "+str(Z))
print ("Final answer: ("+str(X)+","+str(Y)+","+str(Z)+")")

                       #prompt for termination on return

print ("Please record all information you need.")
input("Please press enter to close")

---

### Post by need more pyton on 2010-01-15
I just discovered that my function abort() is returning strings for all my variables even when they should be integers that may be doing something.

by tomorow ill have a new definition for abort() which should be returning integers, that may help

---

### Post by Can+~ on 2010-01-15
[PHP]kill = ["kill", "kilL", "kiLl", "kiLL", "kIll", "kIlL", "kILl", "kILL", "Kill", "KilL", "KiLl", "KiLL", "KIll", "KIlL", "KILl", "KILL"]
for form in kill:
    if k == form:
        K = input ("do you want to abort? Y/N")
        if K == "Y":[/PHP]

It sometimes surprises me that people reach to a certain solution, that it's complex, and never question if there's an easier way. In this case, instead of trying every possible combination to match the input, why not convert the input to a known form?

[PHP]
query = input("What do you want to do:")

if query.lower().strip() == "kill":
    query = input("Do you want to abort?")[/PHP]

Matching the lowercase covers all possibilites (And strip in case of random spaces like "kill "). Also, instead of "aborting" everything, why not wrap it in another way, so that the function already performs this action. Also, read on dictioanries, lists, and the array module. This are basic data structures that can improve the performance/rediability (and therefore, scalability) of your code.

Here's a simple example of having a dictionary that holds references to functions:

[PHP]#!/usr/bin/env python3

import sys

def showhelp():
	"""Shows help to the user"""
	
	print("""--------- help ---------
	Use either quit or exit to leave the application
	blah blah, more help""")

def close():
	"""Closes the application"""
	
	print("Shutting down")
	sys.exit()

def request(question):
	"""Asks a user a certain question, that can be escaped with a command"""
	
	response = input(question).lower().strip()
	
	# Try to see if it's a known command, retrieve the function and perform it.
	if response in actions:
		actions[response]()
	
	return response

actions = \
{
	"help":showhelp,
	"quit":close,
	"exit":close
}

# Example usage
request("Do you like noodles?")[/PHP]

It uses more clear variable names, wraps the common task (checking if user types a certain command) inside a function, so you avoid repetition, etc.

You should really work harder the code, and your variable names. Have fun.

---

### Post by need more pyton on 2010-01-16
can+~
thank you for that code.  I'm still very new to python and programming in general, many of the more involved techniques are still beyond me like that dictionary you showed.  Also I'm aware of the crudity of this program, it is just a personal thing I'm toying with to keep myself busy programming also this particular project is still in its early stages far from complete as you obviously noticed.  
Thank you again for your contribution.

---

### Post by need more pyton on 2010-01-17
thank you all for your help Can+~ i applied some of what you gave me that was very helpful.  in the end i created a big mess of function which probably can should and will be simplified the result of which was that all of my variables had the data type they should have and now my error has disappeared

---

