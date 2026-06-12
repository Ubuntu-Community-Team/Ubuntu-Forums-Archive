---
title: "so my first python program over 15 lines long.."
date: 2007-03-11
forum: Programming Talk
---

### Post by billdotson on 2007-03-11
here is my code:

```

def divide():
	a = input("Input a number for the numerator. " , )
	b = input("Input a number for the denominator. " , )
	# a , / , b , = are separated because they are not all variables or all strings.
	print a , "/" , b , "=" , a / b , "R" , a % b

def multiply():
	a = input("Input a number. " , )
	b = input("Input a second number. " , )
	# a , * , b , = are separated because they are not all variables or all strings.
	print a , "*" , b , "=" , a * b 

def exp():
	a = input("Input a number to raise to a power. " , )
	b = input("Input a number for the exponent. " , )
	# a , ** , b , = are separated because they are not all variables or all strings.
	print a , "**" , b , "=" , a ** b 

def add():
	a = input("Input the first number. " , )
	b = input("Input the second number. " ,  )
	# a , + , b , = are separated because they are not all variables or all strings.
	print a , "+" , b , "=" , a + b 

def interest():
	p = input( "What is your initial investment (input a number) ? $" , )
	r = input( "What is your rate of interest (Example: for 5.75% interest rate enter 5.75)? " , )
	t = input( "How many years will your money be invested? " , )
	n = input( "How many interest payments will you receive a year (compounding interest payments) ? " , )
	i = r/100.0
	#print p
	#print r
	#print t
	#print n
	#print i
	money = float (p * (1+(i/n))**(n*t))
	print
	print "So after a period of" , t ,"year/years" , " with your original investment of $" , p , "gaining at an interest rate of" , r , "% will have $" , money
	print "So in" , t , "years you have gained $" , money - p

def minus():
	a = input("Input the first number. " , )
	b = input("Input the second number. " ,  )
	# a , - , b , = are separated because they are not all variables or all strings.
	print a , "-" , b , "=" , a - b 


print "-Type exp() to raise a number to an exponent."
print "-Type multiply() to multiply two numbers."
print "-Type add() to add two numbers."
print "-Type interest() to calculate gains on interest rates."
print "-Type divide() to divide two numbers."
print "-Type minus() to subtract a number from another."
print "-To use different operations in a certain order type"
print "them in the order and separate them by"
print "a space, a comma and another space"
print

input()

```

I know that I shouldn't do money as a floating point in the interest program and that I shouldn't use input() as you can just type any python command in there and it will execute it. 
Although I do not know how to do money anyway other than a floating point and if I try to use raw_input() when using my variables e.g. a = input() and have a / 5 it says that string is not valid for the "/" operand.

Are there any other recommendations?

Thanks.

---

### Post by Ramses de Norre on 2007-03-11
You need to convert the string to an integer then, like this: ```

try:
    int(raw_input())
except ValueError:
    print "Could not convert data to an integer."
    sys.exit()

```
The try stuff is to handle errors when the string isn't an integer (wrong input).

---

### Post by billdotson on 2007-03-11
so what.. so I do I do something like this??

```

def divide():
	a =try:
                  int(raw_input("Input a number for the numerator. " , ))
             except ValueError:
                  print "Could not convert data to an integer."
                  sys.exit() 
	b =try:
                  int(raw_input("Input a number for the denominator. " , ))
             except ValueError:
                  print "Could not convert data to an integer."
                  sys.exit() 
	# a , / , b , = are separated because they are not all variables or all strings.
	print a , "/" , b , "=" , a / b , "R" , a % b

```

Man I am getting frustrated w/ Python.. I am only doing math stuff because that is the only thing I understand how to do because the math functions are built in.

---

### Post by pmasiar on 2007-03-11
> **billdotson said:**
> Man I am getting frustrated w/ Python.. I am only doing math stuff because that is the only thing I understand how to do because the math functions are built in.

Standard Python distro comes with chock-full of preinstalled packages, including CGI, regular expression, simple database (SQLite) [and others](http://docs.python.org/modindex.html). If it is not build-in function, it does not mean is is hard to get - ie. "import cgi" is all you need for CGI. Try  lists, dictionaries, parsing files - thats where flexibility of Python data structures shines, math calculation is as boring as in any other language, nothing special.

---

### Post by billdotson on 2007-03-12
yeah.. I am in Windows.. my PC is down and I cannot boot anything other than XP on this PC (well I could but the owner of it doesn't want me to)

---

### Post by pmasiar on 2007-03-12
But you do have Python isnstalled, right? Python in Windows has almost all the same default modules like in Linux. Strat IDLE >> Help >> Python Docs >> Global module index. All these goodies are avalibale on Windows, and Linux too.

---

### Post by Ramses de Norre on 2007-03-12
Try this:
```

def divide():
	try:
            a=int(raw_input("Input a number for the numerator. " , ))
        except ValueError:
            print "Could not convert data to an integer."
            sys.exit() 
        try:
            b=int(raw_input("Input a number for the denominator. " , ))
        except ValueError:
            print "Could not convert data to an integer."
            sys.exit() 
	# a , / , b , = are separated because they are not all variables or all strings.
	print a , "/" , b , "=" , a / b , "R" , a % b

```

You can't assign a try statement to a variable, you might want to read up on exception handling because that's what's the try - except stuff is about. In the try block you execute code which could generate an exception (here: when the string can't be converted) if such an exception appears the interpreter jumps out of the try block to the except block matching the thrown exception (in this case ValueError), and executes the code in there.
So if you enter 'a' instead of an int now, you'll see the printed lines and the program will exit.
When the try block gets executed without any error, the interpreter skips the excep block and continues after it.

And programming can be hard in the beginning... The only way to get more advanced is by reading and trying.

PS: you can do it without the try-except too, but you'll get an ugly error on the console when the input isn't a string.

---

### Post by ghostdog74 on 2007-03-12
> **Ramses de Norre said:**
> Try this:
```

......
	try:
            a=int(raw_input("Input a number for the numerator. " , ))
        except ValueError:
            print "Could not convert data to an integer."
            sys.exit() 
     .....

```
.

Using float() instead of int() may be better for decimal inputs used in division. If not, truediv() from operator module or from __future__ import division can be used for whole numbers.

---

### Post by billdotson on 2007-03-12
ok here is the revised code:

```

def divide():
	try:
		a = float(raw_input("Input a number for the numerator. " , ))
        except ValueError:
        	print "Could not convert data to an integer."
       		sys.exit() 
	try:
		b = float(raw_input("Input a number for the denominator. " , ))
        except ValueError:
        	print "Could not convert data to an integer."
       		sys.exit() 
	# a , / , b , = are separated because they are not all variables or all strings.
	print a , "/" , b , "=" , a / b , "R" , a % b

def multiply():
	try:
		a = float(raw_input("Input a number. " , ))
	except ValueError:
        	print "Could not convert data to an integer."
       		sys.exit() 
	try:
		b = float(raw_input("Input a second number. " , ))
	except ValueError:
        	print "Could not convert data to an integer."
       		sys.exit() 
	# a , * , b , = are separated because they are not all variables or all strings.
	print a , "*" , b , "=" , a * b 

def exp():
	try:
		a = float(raw_input("Input a number to raise to a power. " , ))
	except ValueError:
        	print "Could not convert data to an integer."
       		sys.exit() 
	try:
		b = float(raw_input("Input a number for the exponent. " , ))
	except ValueError:
        	print "Could not convert data to an integer."
       		sys.exit() 
	# a , ** , b , = are separated because they are not all variables or all strings.
	print a , "**" , b , "=" , a ** b 

def add():
	try:
		a = float(raw_input("Input the first number. " , ))
	except ValueError:
        	print "Could not convert data to an integer."
       		sys.exit() 
	try:
		b = float(raw_input("Input the first number. " , ))
	except ValueError:
        	print "Could not convert data to an integer."
       		sys.exit() 
	# a , + , b , = are separated because they are not all variables or all strings.
	print a , "+" , b , "=" , a + b 

def interest():
	p = input( "What is your initial investment (input a number) ? $" , )
	r = input( "What is your rate of interest (Example: for 5.75% interest rate enter 5.75)? " , )
	t = input( "How many years will your money be invested? " , )
	n = input( "How many interest payments will you receive a year (compounding interest payments) ? " , )
	i = r/100.0
	#print p
	#print r
	#print t
	#print n
	#print i
	money = int(p * (1+(i/n))**(n*t))
	print
	print "So after a period of" , t ,"year/years" , " with your original investment of $" , p , "gaining at an interest rate of" , r , "% will have $" , money
	print "So in" , t , "years you have gained $" , money - p

def minus():
	try:
		a = float(raw_input("Input the first number. " , ))
	except ValueError:
        	print "Could not convert data to an integer."
       		sys.exit() 
	try:
		b = float(raw_input("Input the second number. " ,  ))
	except ValueError:
        	print "Could not convert data to an integer."
       		sys.exit() 
	# a , - , b , = are separated because they are not all variables or all strings.
	print a , "-" , b , "=" , a - b 


print "-Type exp() to raise a number to an exponent."
print "-Type multiply() to multiply two numbers."
print "-Type add() to add two numbers."
print "-Type interest() to calculate gains on interest rates."
print "-Type divide() to divide two numbers."
print "-Type minus() to subtract a number from another."
print "-To use different operations in a certain order type"
print "them in the desired order, and separate them by"
print "a space, a comma and another space"
print

input()

```

and here are some things I tried after editing the code..

```


C:\Documents and Settings\Bob\Desktop>python math.py
-Type exp() to raise a number to an exponent.
-Type multiply() to multiply two numbers.
-Type add() to add two numbers.
-Type interest() to calculate gains on interest rates.
-Type divide() to divide two numbers.
-Type minus() to subtract a number from another.
-To use different operations in a certain order type
them in the desired order, and separate them by
a space, a comma and another space

divide()
Input a number for the numerator. 5
Input a number for the denominator. 7
5.0 / 7.0 = 0.714285714286 R 5.0

C:\Documents and Settings\Bob\Desktop>python math.py
-Type exp() to raise a number to an exponent.
-Type multiply() to multiply two numbers.
-Type add() to add two numbers.
-Type interest() to calculate gains on interest rates.
-Type divide() to divide two numbers.
-Type minus() to subtract a number from another.
-To use different operations in a certain order type
them in the desired order, and separate them by
a space, a comma and another space

minus()
Input the first number. exit()
Could not convert data to an integer.
Traceback (most recent call last):
  File "math.py", line 99, in <module>
    input()
  File "<string>", line 1, in <module>
  File "math.py", line 78, in minus
    sys.exit()
NameError: global name 'sys' is not defined


```

why.. when I enter something other than a number does it say global name 'sys' not defined? Isn't sys a built-in function?

Also, when the divide() function is called the end of it is 'print a , "/" , b , "=" , a / b , "R" , a % b'
but it shows the remainder being 5.0 when it is evaluated??

I would eventually want to turn this program into a GUI calculator/loan or interest evaluator but my short term goals are as follows:

At the end of my code I have input() so the user can type in the function of their choice e.g. divide(), exp() and so on.  Any command code could be entered in here but I would like to make it where the functions included in the program are the only functions that can be called.

Have interest so that the money is not calculated in floating point but instead is dont using int(), but having the 2 decimal places at the end.

Having the program not terminate when a function is evaluated.
   As you have seen above if someone calls divide() and then puts their numbers in and gets the answer it exits the program.  
I would like to have it where it would stay within the program and at the end of every evaluation give the user a choice to Exit or to not exit.. or either have it where they can enter a command to exit at anytime they want to [use exit()?] 

As I have already started the program I would like to take it as far as I can.  I am going to assume that I will learn more having a goal in mind w/ a program I am trying to make and attempting to get it where I want it to be than just to read and do all of the tutorials in order in a Python manual.

Thanks guys.

---

### Post by Ramses de Norre on 2007-03-12
I can help you with some stuff (I used python for the first time myself a week ago...):

1) Type ```
import sys
``` in the beginning, it's a built in but not in the default namespace.

2) I guess the "5.0" representation is due to the number being float.

3) Instead of just input() you can use a while true loop to keep iterating, in the loop you then parse the input as execute a function or end the program. I'm not sure how to go about that in python though.

---

### Post by kano on 2007-03-12
You need to import sys.
```

import sys

```

If all you need sys for is to exit, you can just do 
```

from sys import exit

```
and replace you sys.exit() 's with exit()

---

### Post by billdotson on 2007-03-12
I was talknig to someone earlier about this and he said that if I had it where say for instance I had this program running on a webserver and had it where they could freely input commands they do do something like delete some of my folders or gain some sort of system access.  So if I have exit imported from sys and they type something other than a number when it exits would it exit into my desktop or something or just exit the program if they try to enter anything other than a number (I am guessing the second)?

thanks.

---

### Post by Tuna-Fish on 2007-03-12
I answered with a pm, but I might as well put it here too:
[QUOTE=billdotson]So if I wanted to get it the way you suggested where raw_input() was used so only numbers and such could be entered there and to get the money thing set up so it is not a floating point how would I go about it? And I understand that this is my first simple program and that these things don't really matter as of right now but later on they would.
[/quote]

First, to do money as integer simply place it so that the smallest meaningful unit of money, usually one cent or one penny or whatever, is 1. So, 1 dollar, would be 100, 15 dollars is 1500 etc.
Then you have to write a few functions to convert money to and from the decimal notation:

Save as pythonmoney.py into same dir you're working in
```

#! /usr/bin/python
# coding=UTF-8
#####################
# pythonmoney.py
# a quick script that helps handling money as long
# use, distribute or modify this any way you want
# author=Antti-Ville Tuunainen
# version=12.3.2007

# This function takes a long or int as argument, 
# and returns a string that looks like money.
# You can then print that string, save it to a file, or whatever.
#
# Things to look for in this function: % between numerical values 
# means give remainder,but between a string and a list it means
# format these values into the string
#
# Actually, I lied a bit there, (dollars,pennies) isn't a list, but a tuplet. 
# This however, isn't really significant.
def moneystring(m):
	dollars = m/100
	pennies = m%100
	if (pennies <10):
		return "%d.0%d" % (dollars,pennies)
	return "%d.%d" % (dollars,pennies)


# This function is the exact opposite of the previous,
# it takes in a string ant tries to spew out a meaningful long.
# if the string inputted into this contains non-number stuff,
# like letters, this throws a ValueError Exception.
# catching this is an exercise left to the caller of this function. 
# (this can be used to make the program ask twice if a bad value is given)
#
# There is a bit of black magic in this function, specifically the (s+".0")
# This guarantees that any meaningful number that looks like 
# money will split into at least 2 parts. If given a string that 
# already has a ".", the string will split into 3 parts. the 3rd part is, 
# however, never read, and is for all meaningful purposes discarded.
# there is one bit of undesired functionality here:
# 123.456 will parse into a mess. Perhaps fixed in a later release? 
def parsemoney(s):
	h = (s+".0").split('.')
	m = long(h[1])+100*long(h[0])
	return m

# this is a simple test function. 
# it takes in a string, from which it reads a value of money
# and then it turns it back into a string and prints it out.
def test():
	a=parsemoney(raw_input("how much money? :"))
	print(moneystring(a))

```
Instructions of use: Either:
1. Use as a python module, and save to same dir as your program and type 'import pythonmoney' in the top of your file. you can the access the functions by typing
```

pythonmoney.parsemoney(something)
pythonmoney.moneystring(something)
pythonmoney.test()
```

To make it all look neater, you can also create simple helper functions to ease it's use:
```

import pythonmoney
def printm(m):
        print pythonmoney.moneystring(m)
def m_input(s):
        while(True):
                try:
                        a = pythonmoney.parsemoney(raw_input(s))
                except ValueError:
                        print "That was not a proper value!"
                else:
                        break
	return a
```
Now you can use m_input() and printm() like you would use input() and print(), with the exception that printm only ever takes a single argument, of course...
2: just integrate the functions into your own code and use them directly. that way you get it all in a single file.
> 
Btw when would it be useful to use input() over raw_input()?


When you do want to evaluate the input. Essentially, it is used in the realms of meta-programming, programming programs that produce or modify programs. Making it the standard input() over raw_input() was imho a braindead decision, because python is often used as a glue language, for example for receiving something from a web server and executing a script. in this use if someone does input() over raw_input(), there are serious chances that a malign user can take over the whole machine. As if sql insertions weren't bad enough.

Bit of trivia: when you boot up a python interpreter, the thing you type into is input().

> 
so if I did that above
import sys
and then entered sys.exit() it would shut down my system or something?

no, just the interpreter. sys.exit() is the standard command for exiting a program. Essentially, whenever you run a script trough an interpreter the last character the interpreter reads is an EOF (End-of-File) symbol, which translates to sys.exit().

And sorry it took long, my GF was here over the weekend not much time to code when that happens:)

---

### Post by siman on 2007-03-12
> 
why.. when I enter something other than a number does it say global name 'sys' not defined? Isn't sys a built-in function?


you got several other answers here. they are all true, here is mine:

you write: sys.exit(). and python informs you it doesn't now about "sys" yet. but you probably read on the internet that sys is a module always included in python.. yes it is, but not every programm uses every module that is included in python, so you must tell python "i want to use the sys module", like this "import sys".

if you try (!!) stuff like this, its easier to start up a interaction python session, just start the "Python" programm and you get an input line like this:
```

>>

```

this is a "python interactive session" (or so...), you can write in python-code and it gets executed after you press enter.. great he? for example:

```

>> sys.exit()
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
NameError: name 'sys' is not defined

```

.. you get the error. now we import the module "sys", so python nows about it:
```

>>import sys
>>sys.exit()

```
great.. that worked... see, easy to work this kind of stuff out with an interactive-session.

----------------------------
> 
Also, when the divide() function is called the end of it is 'print a , "/" , b , "=" , a / b , "R" , a % b' but it shows the remainder being 5.0 when it is evaluated??


i dont get that, whats wrong :-)
----------------------------
> 
At the end of my code I have input() so the user can type in the function of their choice e.g. divide(), exp() and so on.  Any command code could be entered in here but I would like to make it where the functions included in the program are the only functions that can be called.


good goal!! but this will be easier, when you get rid of the input() function. take a closer look, what it does (i used the interactive-session again):

```

>>help("input")
Help on built-in function input in module __builtin__:

input(...)
    input([prompt]) -> value
    
    Equivalent to eval(raw_input(prompt)).

```

aha!! input() does two things: it calls raw_input() to get what the user typed, and it also calls eval() to evaluted/execute what the user just typed. but you want the user to only be able to use YOUR functions, not any function.

hm, so we must check the input from the user and THEN evalute it (eventually), this could be done like this (again, take a look at what help("input") told us about the input function):

```

userCommand = raw_input() # this is what input() uses too
# now let's see what the user wrote:
if userCommand == "minus":
  minus() # user wrote minus.. lets call minus
elif userCommand == "add":
  add() # aha.. lets call add
elif # check for other commands
....
...
else:
  print "NO! You are not allowed to use this function"

```

----------------------------

> 
Have interest so that the money is not calculated in floating point but instead is dont using int(), but having the 2 decimal places at the end.


... well, you might not like it :-) but I as well advise you to use cents not dollars. dont worry about converting those... just input all values as cents, and output them as cents. you can worry about how the money-values get display / input later... 
----------------------------
> 
Having the program not terminate when a function is evaluated.


hint: use a loop, something like this:

```

while continueUsingProgram == 1:
  print "-Type exp() to raise a number to an exponent."
  print "... etc"
  userCommand = raw_input()
  if userCommand == "minus":
    # we already talked about that part.. see above
  
     ## NEW, check if userCommand is "exit"
  elif userCommand == "exit":
     sys.exit() # or you could write continueUsingProgram = 0 .. think about it :-)

```

read about loops.. I'm not sure how clear this example is.
----------------------------
> I am going to assume that I will learn more having a goal in mind w/ a program I am trying to make and attempting to get it where I want it to be


YES!!! This is what keeps you motivated.

---

