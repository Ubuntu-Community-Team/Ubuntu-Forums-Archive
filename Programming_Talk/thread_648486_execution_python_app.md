---
title: "execution python app"
date: 2007-12-23
forum: Programming Talk
---

### Post by kool_kat_os on 2007-12-23
I just wrote this app on Python:
This is how it is saved

[HTML]Python 2.5.1 (r251:54863, Apr 18 2007, 08:51:08) [MSC v.1310 32 bit (Intel)] on win32
Type "copyright", "credits" or "license()" for more information.

    ****************************************************************
    Personal firewall software may warn about the connection IDLE
    makes to its subprocess using this computer's internal loopback
    interface.  This connection is not visible on any external
    interface and no data is sent to or received from the Internet.
    ****************************************************************
    
IDLE 1.2.1      
>>> # Area Calculation Program
>>> print "Welcome to the Area Calculation Program"
Welcome to the Area Calculation Program
>>> print "-------------"
-------------
>>> # Print out this menu:
>>> print "Please select a shape:"
Please select a shape:
>>> print "1 Rectangle"
1 Rectangle
>>> print "2 Circle"
2 Circle
>>> # Get the user's choice:
>>> shape = input("> ")
> 2
>>> # Calculate the Area:
>>> if shape == 1:
	height = input("Please enter the height: ")
	width = input("Please enter the width: ")
	area = height*width
	print "The Area is", area,"units"
else:
	radius = input("Please enter the radius")
	area = 3.14*(radius**2)
	print "The area is", area,"units"

	
Please enter the radius8
The area is 200.96 units
>>> [/HTML]

How do I make this app run in dos on windows? When I click on the file(its named: area.py)the dos pops up for a second and goes away. What am I doing wrong?

---

### Post by scxtt on 2007-12-23
you would have to have python installed in windows ...

---

### Post by kool_kat_os on 2007-12-23
I do have it on windows

---

### Post by scxtt on 2007-12-23
you mention "dos" so it led me to believe you just expected a python script to run in dos ... the code you posted looks more like an interactive python session - you'd need to clean it up to be able to run it like:

python area.py

or load it up in windows.

---

### Post by Mr.popo on 2007-12-23
maybe put
  
input(" ") or raw_input(" ")

at the end of the code and try again.

---

### Post by scxtt on 2007-12-23
i installed python 2.5.1 on my 2k3 VM ... i've never used python in windows before - so that was a new experience :p ... i copied over your area.py (w/o all the >>> and input) and it runs fine ... are you expecting IDLE to run it using the example input in your code?  if i just click on area.py, it runs waiting for input - but as soon as it prints the area, it exits closing the window ... which is most likely where Mr.popo's suggestion is useful.

---

### Post by kool_kat_os on 2007-12-23
> scxtt  	
Re: execution python app
i installed python 2.5.1 on my 2k3 VM ... i've never used python in windows before - so that was a new experience ... i copied over your area.py (w/o all the >>> and input) and it runs fine ... are you expecting IDLE to run it using the example input in your code? if i just click on area.py, it runs waiting for input - but as soon as it prints the area, it exits closing the window ... which is most likely where Mr.popo's suggestion is useful.

Can you upload the file that you used to this thread, thanks

---

### Post by Mr.popo on 2007-12-23
Try this:

```


# Area Calculation Program
print "Welcome to the Area Calculation Program"
print "-------------"

# Print out this menu:
print "Please select a shape:"
print "1 Rectangle"
print "2 Circle"
# Get the user's choice:
shape = input("> ")
# Calculate the Area:
if shape == 1:
	height = input("Please enter the height: ")
	width = input("Please enter the width: ")
	area = height*width
	print "The Area is", area,"units"
else:
	radius = input("Please enter the radius")
	area = 3.14*(radius**2)
	print "The area is", area,"units"
input(" ")

```

That should work

---

### Post by kool_kat_os on 2007-12-23
It does, Thanks alot

---

### Post by scxtt on 2007-12-23
i did something like this:
```
# Area Calculation Program
print "Welcome to the Area Calculation Program"
print "-------------"
# Print out this menu:
print "Please select a shape:"
print "1 Rectangle"
print "2 Circle"
# Get the user's choice:
shape = input("> ")
# Calculate the Area:
if shape == 1:
        height = input("Please enter the height: ")
        width = input("Please enter the width: ")
        area = height*width
        print "The Area is", area,"units"
else:
        radius = input("Please enter the radius: ")
        area = 3.14*(radius**2)
        print "The area is", area,"units"

[COLOR="Red"]done = ""
while done != "q":
        done = raw_input("Type q to quit: ")
exit()[/COLOR]
```
i haven't done much w/ python in a while - esp. in windows - that was kinda "fun" :)

---

### Post by kool_kat_os on 2007-12-23
Hi , I messed up again. 

here is a new code that I just made and it has the same problem:

[HTML]# Area Calculation Program
print "Welcome to the Area Calculation Program"
print "-------------"

# Print out this menu:
print "Please select a shape:"
print "1 Rectangle"
print "2 Circle"
# Get the user's choice:
shape = input("> ")
# Calculate the Area:
if shape == 1:
	print "1 Area"
	print "2 Perimeter"
        #Get the user's choice:
	calc = input("> ")
	# Calculate
        if calc == 1:
                height = input("Please enter the height: ")
                lenght = input("Please enter the lenght: ")
                area = lenght*height
                print "The area is", area,"units"
        if calc == 2:
                height = input("Please enter the height: ")
                lenght = input("Please enter the lenght: ")
                perimeter = (lenght+height)*2
                print "The perimeter is", perimeter,"units"
if shape == 2:
	print "1 Area"
	print "2 Perimeter"
	#Get the user's choice:
	calc1 = input("> ")
	# Calculate
        if calc1 == 1:
                radius = input("Please enter the radius: ")
                area = 3.14*(radius**2)
                print "The Area is", area,"units"
        if calc1 == 2:
                radius = input("Pleas enter the radius: ")
                perimeter = 2*3.14*radius
                print "The perimeter is"), perimeter,"units"

input(" ")
[/HTML]

Now whats wrong with this one?

---

### Post by scxtt on 2007-12-23
> **kool_kat_os said:**
> Now whats wrong with this one?
```
print "The perimeter is"[COLOR="Red"])[/COLOR], perimeter,"units"
```
you've got an extra ")" at the very least

{ and length is spelled wrong ;) }

---

### Post by kool_kat_os on 2007-12-23
thanks, it works now

---

### Post by kool_kat_os on 2007-12-23
I know I am asking too many questions, but I have another: 
how would I convert this code to a C++ code?

[HTML]# Calculation Program
print "Welcome to the Shape Calculation Program"
print "-------------"

# Print out this menu:
print "Please select a shape:"
print "1 Rectangle"
print "2 Circle"
# Get the user's choice:
shape = input("> ")
# Calculate the Area:
if shape == 1:
	print "1 Area"
	print "2 Perimeter"
        # Get the user's choice:
	calc = input("> ")
	# Calculate
        if calc == 1:
                height = input("Please enter the height: ")
                length = input("Please enter the length: ")
                area = length*height
                print "The area is", area,"units"
        if calc == 2:
                height = input("Please enter the height: ")
                length = input("Please enter the length: ")
                perimeter = (length+height)*2
                print "The perimeter is", perimeter,"units"
if shape == 2:
	print "1 Area"
	print "2 Perimeter"
	# Get the user's choice:
	calc1 = input("> ")
	# Calculate
        if calc1 == 1:
                radius = input("Please enter the radius: ")
                area = 3.14*(radius**2)
                print "The Area is", area,"units"
        if calc1 == 2:
                radius = input("Please enter the radius: ")
                perimeter = 2*3.14*radius
                print "The perimeter is", perimeter,"units"
input(" ")
[/HTML]

Thanks(again):)

---

### Post by LaRoza on 2007-12-23
> **kool_kat_os said:**
> I know I am asking too many questions, but I have another: 
how would I convert this code to a C++ code?


Rewrite it in C++/.

---

### Post by kool_kat_os on 2007-12-23
I know that, but what would I change what to is what I dont know.

---

### Post by scxtt on 2007-12-23
i'm pretty sure to convert python to C++ you'll need to learn C++ . . . ;)

---

### Post by kool_kat_os on 2007-12-23
oh man.... I have a long wayz to go

---

### Post by scxtt on 2007-12-23
i'm sure it wouldn't be too complicated, but if you don't know C++ at all, probably a bit trying of an experiment ... you're doing basic stuff like printing text, reading in values, then just performing basic calculations on them ... i bet you'd just need to use:

#include <iostream>
#include <cmath>

---

### Post by kool_kat_os on 2007-12-23
Can someone give me an example because I dont know what im doing in c++.

Thanks

---

### Post by LaRoza on 2007-12-23
> **kool_kat_os said:**
> Can someone give me an example because I dont know what im doing in c++.

Thanks

Don't over reach.

Why do you want to rewrite this in a language you don't know?

If you want to learn the languages, see my wiki. Debugging and learning should take up a lot of your time if you wish to program.

---

### Post by Mr.popo on 2007-12-24
Why would you want to convert that python code to c++?

Just stick with python.

---

### Post by samjh on 2007-12-24
It's because he wants to get into game programming, I think.

C++ is a huge language and takes years to learn.  If you're very bright, you might learn it well enough in several months.  Most people takes years.

Aim for the target you can hit.  It seems you are very new to programming in general.  Just stick to Python for the time being.  After you've gotten comfortable with basic programming concepts, like functions, iteration, selection, recursion, etc., then you might want to take baby steps into C or C++.

Learn to crawl, walk, and run, before you jump! :)

If you are really determined to learn C++, then forget about making games for a while.  Start from the very basics.  Use this tutorial: [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)
Make sure to install the compiler by doing this in your terminal: ```
sudo apt-get install build-essential
```.  To compile using the g++ compiler: ```
g++ -o myprogram myprogram.cpp
```That command will compile myprogram.cpp into an executable file named myprogram.  The -o switch is used to specify the name of the output file (in this case, the executable, myprogram).

---

### Post by kool_kat_os on 2007-12-24
I,m unfortunatly using windows, the program I use is dev cpp

---

### Post by kool_kat_os on 2007-12-24
should I learn C first or C++ or  does it matter?

---

### Post by LaRoza on 2007-12-24
> **kool_kat_os said:**
> I,m unfortunatly using windows, the program I use is dev cpp

Dev CPP is very good and you can use it through the command line. It used gcc and g++ just like Linux.

---

### Post by LaRoza on 2007-12-24
> **kool_kat_os said:**
> should I learn C first or C++ or  does it matter?

Whatever you want. There is a big debate about this.

Here is the caveat: They are not the same language and require a different mindset. I like C personally, but I studied C++ first.

---

### Post by Wybiral on 2007-12-24
> **LaRoza said:**
> Dev CPP is very good and you can use it through the command line. It used gcc and g++ just like Linux.

Dev-C++ is very good if you have to use Windows (and still want GCC), I also recommend Code::Blocks (similar to Dev-C++, with some different features).

---

### Post by Majorix on 2007-12-24
I believe actually the devs of DevC++ (what I used when I used to code with C++ under Windows) left that project 3 years ago or so and joined Code::Blocks. I, however, couldn't get used to Code::Blocks for some reason. You should try it though. Good luck.

---

