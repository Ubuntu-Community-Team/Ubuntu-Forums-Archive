---
title: "Executing files"
date: 2007-12-22
forum: Programming Talk
---

### Post by kool_kat_os on 2007-12-22
I just wrote this with python on windows:

```
    
>>> # Area calculation program
>>> print "Welcome to the Area calculation program"
Welcome to the Area calculation program
>>> print "________"
________
>>> print

>>> # Print out the menu:
>>> print "Please select a shape:"
Please select a shape:
>>> print "1 Rectangle"
1 Rectangle
>>> print "2 Circle"
2 Circle
>>> # Get the user&#8217;s choice:
>>> shape = input("> ")
> 1
>>> # Calculate the area:
>>> if shape == 1:
	height = input("Please enter the height: ")
	width = input("Please enter the width:  ")
	area = height*width
	print "The Area is", area
else:
	radius = input("Please enter the radius: ")
	area = 3.14*(radius**2)
	print "The area is", area	
>>> 
```

I saved it as .py, is there any way to make it run in the command prompt in windows? 
when I click on the file the command prompt pops up for now even a second and goes away and nothing happens.

---

### Post by dwhitney67 on 2007-12-22
I just answered a similar question for another post.

If using Gnome, right click on your desktop's background to create a launcher.  If you are using KDE, then I'm sure it is something similar, however I do not know for sure.

---

