---
title: "Python: TypeError: 'int' object is not callable"
date: 2009-08-18
forum: Programming Talk
---

### Post by pauelmaco on 2009-08-18
Hello

I'm learning a bit of python, and to learn I'm doing a very simple programa that does some operations. But I get an error when I'm trying to use the "factorial" function. Here is the code:

> # 
#This is a very simple program
#

bloca = 1

def factorial(a):
	if a == 0:
		return 1
	else:
		return a * factorial(a-1)

a = 0
		
tria = 0

ajuda = 1

suma = 2
sumaajuda = 200

resta = 3
restaajuda = 300

factorial = 4
factorialajuda = 400

	#Start information
	
print "Simple program, version 0.01"
print "To get help, type'ajuda'"
	
while bloca == 1:

	print " "

	#Now the "promp" appears

	tria = input("#>>> ")

	if tria == 1:
		print "This only can do some simple operations"
		print "Possible commands are:"
		print " "
		print " suma","    factorial"
		print " resta"
		print " "
		print "To get help, put 'ajuda' next the command"
		print " "
		print "    sumaajuda  (This will help you about suma)"
		print " "

	if tria == 2:
		print " "
		ab = input("Add this: ")
		a = input("To this: ")
		print ab, "+", a, "=", ab +a
	if tria == 200:
		print " "
		print "This command is to add numbers"

	if tria == 3:
		print " "
		num1 = input("Treu aixo: ")
		num2 = input("A aixo: ")
		print num2, "-", num1, "=", num2 -num1
	if tria == 300:
		print " "
		print "This command is to ...."
		
	if tria == 4:
		print " "
		a = input("Put a number: ")

		print factorial(a)
		

And I get an error like this:

> #>>> factorial
 
Put a number: 5
Traceback (most recent call last):
  File "interpret.py", line 84, in <module>
    print factorial(a)
TypeError: 'int' object is not callable

Pleas, help me!!

Thanks> 

---

### Post by Arndt on 2009-08-18
> **pauelmaco said:**
> Hello

I'm learning a bit of python, and to learn I'm doing a very simple programa that does some operations. But I get an error when I'm trying to use the "factorial" function. Here is the code:


		

And I get an error like this:



Pleas, help me!!

Thanks

(If you had put the code inside CODE tags, not QUOTE tags, the quoting would work better here, and it would have been correctly indented, too.)

I think you define 'factorial' first as a function, but then override it by the assignment factorial=4. From that point on, it's an integer, and the function is gone.

---

### Post by pauelmaco on 2009-08-18
> **Arndt said:**
> (If you had put the code inside CODE tags, not QUOTE tags, the quoting would work better here, and it would have been correctly indented, too.)

I think you define 'factorial' first as a function, but then override it by the assignment factorial=4. From that point on, it's an integer, and the function is gone.

THANK YOU VERY MUCH. I now understand the problem!! :P:P:P

---

