---
title: "[SOLVED] Beginner python program help"
date: 2008-08-19
forum: Programming Talk
---

### Post by andrewoftheelves on 2008-08-19
hey, I'm new to python and still getting used to the syntax. Does anyone know what I'm doing wrong here? I was trying to find a do-while statement but had to settle with using a while statement and then doing, if not equal then break. Haha I know that it's messy and it dosn't even work but I still need help.  
[PHP]#!/usr/bin/python
import random, math

again = "y"
x= (random.randint(1,10))

while (again =="y"):
 
 guess = 0 
 guess = input("roll the dice and make a guess, this dice is 100 sided: ")

 if (guess<x):
	print "less than the number"
 elif (guess>x):
	print "greater than the number"
 else:
	print " BIG MONEY"
	again = input("try again? type y for yes.")
 if (again != "y"): break;


[/PHP]

---

### Post by LaRoza on 2008-08-19
What is the problem? Besides the misuse of input().

Use raw_input()

---

### Post by andrewoftheelves on 2008-08-19
File "python.py", line 18, in <module>
    again = input("try again? type y for yes.")
  File "<string>", line 1, in <module>
NameError: name 'y' is not defined


I get that error.

---

### Post by andrewoftheelves on 2008-08-19
thanks very much LaRoza, that fixed it.

---

### Post by andrewoftheelves on 2008-08-19
[PHP]#!/usr/bin/python
import random, math

again = "y"
#makes a random number between and including 1 and 10
x= (random.randint(1,10))

while (again =="y"):
 
 guess = 0 
 guess = input("roll the dice and make a guess, this dice is 100 sided:")

 if (guess<x):
	print "less than the number"
 elif (guess>x):
	print "greater than the number"
 else:
#if the user's guess is right they have the choice to stop or continue playing with a new die.	
	print " BIG MONEY"
	again = raw_input("try again? type y for yes.")
 	if (again != "y"): 
		print "Thanks for playing"
		break
	else : 
		x= (random.randint(1,10))



 
 

	

[/PHP]

My finished product. Thanks again LaRoza

---

### Post by Wybiral on 2008-08-19
> **andrewoftheelves said:**
> thanks very much LaRoza, that fixed it.

Yes, "input" is evaluated, "raw_input" simply returns a string. Generally, you never want to use "input".

For example:
```

data = input()

```
In the prompt, enter something like:
```

__import__("sys").stdout.write(str(__import__("os").listdir("./")))

```

---

### Post by pmasiar on 2008-08-19
> **Wybiral said:**
> Yes, "input" is evaluated, "raw_input" simply returns a string. Generally, you never want to use "input".

In Python 3.0, input() would work like raw_input(), eliminating the confusion.

---

