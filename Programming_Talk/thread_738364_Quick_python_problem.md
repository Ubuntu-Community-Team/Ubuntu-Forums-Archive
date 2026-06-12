---
title: "Quick python problem"
date: 2008-03-28
forum: Programming Talk
---

### Post by Jon11393 on 2008-03-28
I'm learning Python and decided to script an adding program. The use enters the first number, and then the second. After he inputs the data the computer adds both the numbers together and prints the solution. 

The problem is that the computer just puts both the numbers next to each other instead of adding them. Could anyone please help me with this simple problem?

[B]
#! /usr/bin/python 
print "I'm going to add two numbers!"
x = raw_input("First: ")
y = raw_input("Second: ")
print "Okay, the answer is... "
print x+y
[/B]

Is my code, could somone please help me find the error?

---

### Post by LaRoza on 2008-03-28
```

#! /usr/bin/python 
print "I'm going to add two numbers!"
x = raw_input("First: ")
y = raw_input("Second: ")
print "Okay, the answer is... "
print float(x)+float(y)

```

raw_input() returns a string, and you can't perform math on strings.

---

### Post by WinterWeaver on 2008-03-28
try using input rather than raw_input

raw_input reads it as a string.

---

### Post by LaRoza on 2008-03-28
> **WinterWeaver said:**
> try using input rather than raw_input

raw_input reads it as a string.

Don't use input() use raw_input(), because raw_input() reads it as a string.

---

### Post by gnuman on 2008-03-28
Try this:

```

x = int(raw_input("First: "))
y = int(raw_input("Second: "))

```

That will cast the string as an integer.  You could also use other types, like float, etc.

---

### Post by Jon11393 on 2008-03-28
Ah, thank you! I was trying

**int** x = raw_input("yaddayadda")

instead to declare integers as I didnt know what you've told me!

Thanks everyone for the help!

---

### Post by Jon11393 on 2008-03-28
------ deleted -----

---

### Post by LaRoza on 2008-03-28
No closing parentheses.

> choice = int(raw_input("one for addition, two for subtraction: ")

---

### Post by LaRoza on 2008-03-28
This may be better (instead of using numbers for chosing)
[php]
#! /usr/bin/python 

choice = raw_input("+ for addition, - for subtraction: ")

if choice == "+":
	
	print "Im going to add two numbers!"

	x = int(raw_input("First: "))
	y = int(raw_input("Second: "))

	print "Okay, the answer is... "
	print x+y

elif choice == "-":
	
	print "Im going to subtract two numbers!"
	
	a = int(raw_input("First: "))
	b = int(raw_input("Second: "))

	print "The answer is... "
	print a-b

else:
	print "Invalid choice" 
[/php]

---

