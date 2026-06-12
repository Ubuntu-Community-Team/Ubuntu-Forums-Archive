---
title: "Python: end program command &amp; if statement with or"
date: 2008-04-15
forum: Programming Talk
---

### Post by CaptainLinux94 on 2008-04-15
I'm writing a simple console window program that calculates the area of certain shapes.  (Don't worry to much about this, I'm just looking for a few specific questiosn to be answered)

At the start of the program, it prompts the user for what type of shape they want the program to calculate area for.

Let's say they don't have any of the shapes prompted for, this is where I want to create a feature to end the program immediately.  How would I do this?  I'll post the source-code at the bottom of the post.

Also, I want to know how to create an if-statement which checks for multiple arguments such as (in english):

"If variable one is 1, 2, 3, 4, or 5, continue the program."

And last but not least, is there a syntax to continue running the program if an if-statement proves to be true?

Here's my source code:
```

# Area calculation program

print
print "_______________________________________"
print "Welcome to the Area calculation program"
print "_______________________________________"
print

# Print out the menu:
print "Please select a shape:"
print "1 Rectangle"
print "2 Circle"
print "3 Square"
print "4 Parallelogram"
print

# Get the user's shape:
shape = input("Type the corresponding number: ")
print

# Get the user's unit measurement
units = input("Type the unit of measurement(MUST be plural, AND surrounded by quotes): ")
print

# Calculate the area:
# Rectangle
if shape == 1:
	height = input("Please enter the height: ")
	width = input("Please enter the width: ")
	area = height*width
	print
	print "The area is", area, "square", units, "."
	print
# Circle
elif shape == 2:
	radius = input("Please enter the radius: ")
	area = 3.14*(radius**2)
	print
	print "The area is", area, "square", units, "."
	print
# Square
elif shape == 3:
	side = input("Please enter the side length: ")
	area = side*2
	print
	print "The area is", area, "square", units, "."
	print
# Parallelogram
elif shape == 4:
	base = input("Please enter the base: ")
	height = input("Please enter the height: ")
	area = base*height
	print
	print "The area is", area, "square", units, "."
	print
```

---

### Post by Wybiral on 2008-04-15
It sounds like you need to check if some variable exists in a list of numbers? Try this:

```

if x in (0, 1, 2, 3, 4, 5):
    ... do something ...

```

I'm not sure what you mean by "is there a syntax to continue running the program if an if-statement proves to be true?" conditions don't end the program to begin with.

You can end a program immediately using "exit()"

---

### Post by CaptainLinux94 on 2008-04-15
Thanks, and nevermind about the question about the "Continue," function.  All it seems I need was  the exit().

---

### Post by WW on 2008-04-15
> **Wybiral said:**
> 
You can end a program immediately using "exit()"
In Python 2.4, you would use sys.exit():
```

import sys

...

sys.exit()

```

---

### Post by bijupg on 2008-04-16
Hello, try this
(if indentation is not correct plz correct it.)

# Area calculation program

print
print "_______________________________________"
print "Welcome to the Area calculation program"
print "_______________________________________"
print
while 1:
	# Print out the menu:
	print "Please select a shape:"
	print "1 Rectangle"
	print "2 Circle"
	print "3 Square"
	print "4 Parallelogram"
	print

	# Get the user's shape:
	shape = input("Type the corresponding number: ")
	print

	# Get the user's unit measurement
	units = input("Type the unit of measurement(MUST be plural, AND surrounded by quotes): ")
	print

	# Calculate the area:
	# Rectangle

	if shape == 1:
		height = input("Please enter the height: ")
		width = input("Please enter the width: ")
		area = height*width
		print
		print "The area is", area, "square", units, "."
		print
	# Circle
	elif shape == 2:
		radius = input("Please enter the radius: ")
		area = 3.14*(radius**2)
		print
		print "The area is", area, "square", units, "."
		print
	# Square
	elif shape == 3:
		side = input("Please enter the side length: ")
		area = side*2
		print
		print "The area is", area, "square", units, "."
		print
	# Parallelogram
	elif shape == 4:
		base = input("Please enter the base: ")
		height = input("Please enter the height: ")
		area = base*height
		print
		print "The area is", area, "square", units, "."
		print
	else:
		break 
	
	ans = ''
	while ans.upper() != 'Y' and ans.upper() != 'N':
		ans = raw_input("Do you want to continue(Y/N) : ")
	
	if ans.upper() == 'Y':
		continue
	else:
		break

---

### Post by WW on 2008-04-16
> **bijupg said:**
> 
(if indentation is not correct plz correct it.)

You can preserve the indentation in your code by enclosing it in [ code ] and [ /code ] tags (but without the spaces inside the brackets).

---

