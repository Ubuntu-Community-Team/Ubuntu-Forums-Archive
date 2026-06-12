---
title: "How do I set an input value in python?"
date: 2007-02-28
forum: Programming Talk
---

### Post by billdotson on 2007-02-28
Here is my source code for a program to find the circumference of a circle:

import math
def newline():
	print
radius = 4
circle = radius * radius * math.pi
newline()
print "Say the radius of a circle =" , radius  
newline() 
print "To find the circumference we take the value of the radius and square that value, then multipy that result by pi." 
newline()
print "That gives us the circumference of the circle."  
newline()
print "It's circumference is" , circle , "units."
newline()
print "So the equation for the circumference of a circle is circumference = (radius*radius)*pi"

So if I want to have the program so that I can enter my own value for radius while the program is running? Like if I wanted to have a question before any of the other ran that asked "What is the radius of your circle?" and then allowed you to enter any value you wanted for the radius and then radius would then equal that value.

Does that make any sense?  If not I want to have it set up like a formula in a spreadsheet where whatever number you enter for radius changes the value for circumference.  

Later on I was thinking of making a simple program that it's only purpose would be to be calculate interest for your investments.. like how much are you putting in, what is the percentage rate, how long are you going to keep it in there?

---

### Post by pmasiar on 2007-02-28
> **billdotson said:**
>  I can enter my own value for radius while the program is running? Like if I wanted to have a question before any of the other ran that asked "What is the radius of your circle?" 

It is possible and easy: build-in function input() and raw_input() - couple links for you:

[http://www.hetland.org/python/instant-hacking.php](http://www.hetland.org/python/instant-hacking.php)
[input and variables]("http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python/Who_Goes_There%3F") - a chapter from excellent online book

all linked from [http://learnpydia.pbwiki.com/HowToStart](http://learnpydia.pbwiki.com/HowToStart)

---

### Post by po0f on 2007-02-28
billdotson,

It would be a lot easier to read your code if you used the [ code ] tags.  ;)

And there's no need for the newline() function.  Since you have function calls all over the script, why not just make them empty print statements?  Why not get rid of the empty print statements while we're at it?

```
[font="Courier New"]import math

radius = 4
circle = radius * radius * math.pi

print """Say the radius of a circle = %d

To find the circumference we take the value of the radius and square that value, then multipy that result by pi.

That gives us the circumference of the circle.

It's circumference is %d units.

So the equation for the circumference of a circle is circumference = (radius*radius)*pi""" % (radius, circle)[/font]
```

---

### Post by billdotson on 2007-02-28
so how does that work? could you please explain how you got the following code :

[code] print """Say the radius of a circle = %d

To find the circumference we take the value of the radius and square that value, then multipy that result by pi.

That gives us the circumference of the circle.

It's circumference is %d units.

So the equation for the circumference of a circle is circumference = (radius*radius)*pi""" % (radius, circle) [code] 

Could you explain how the %d and all the quotations work, as I am only 2 days into Python and want to actually know what is going on in the code.  Thanks.

---

### Post by pmasiar on 2007-02-28
> **billdotson said:**
> Could you explain how the %d and all the quotations work, as I am only 2 days into Python and want to actually know what is going on in the code.  

which part of explanation from the link I gave you before - [input and variables]("http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python/Who_Goes_There%3F") - you do not understand?

---

### Post by billdotson on 2007-02-28
no I didn't understand what poot was doing with my code.  he replaced 

```
 import math
def newline():
print
radius = 4
circle = radius * radius * math.pi
newline()
print "Say the radius of a circle =" , radius
newline()
print "To find the circumference we take the value of the radius and square that value, then multipy that result by pi."
newline()
print "That gives us the circumference of the circle."
newline()
print "It's circumference is" , circle , "units."
newline()
print "So the equation for the circumference of a circle is circumference = (radius*radius)*pi" 
``` with

```
 import math

radius = 4
circle = radius * radius * math.pi

print """Say the radius of a circle = %d

To find the circumference we take the value of the radius and square that value, then multipy that result by pi.

That gives us the circumference of the circle.

It's circumference is %d units.

So the equation for the circumference of a circle is circumference = (radius*radius)*pi""" % (radius, circle) 
```

---

### Post by Wybiral on 2007-02-28
btw, the code tag works like this...

[ c o d e ]

Code goes here

[ / c o d e ]

Minus the spaces between the letters.


Try running this program:
```

x = raw_input("Enter a value for x: ")
print "You entered: ", x

```
Hopefully that clears it up a bit.

---

### Post by billdotson on 2007-03-01
I understand the input() but I don't understand what he did when he took out all of my newline() functions and empty print statements and replaced them with with a series of quotations and %'s

---

### Post by ghostdog74 on 2007-03-01
> **billdotson said:**
> I understand the input() but I don't understand what he did when he took out all of my newline() functions and empty print statements and replaced them with with a series of quotations and %'s

basically, your newline function looks redundant. A simple print statement with give you a new line.
anyway, you can read [here]("http://www.python.org/doc/1.5.1p1/tut/strings.html") regarding the usage of triple quotes """. He just bring all your print statements inside triple quotes, so you don't need that many print statements.
eg
```

print " ##### My script #####"
print "This is a script done by me"
print " Name: %s  " % "billdotson"

```

could be written like this
```

print """ ##### My script #####
               This is a script done by me
               Name: %s  """ % "billdotson"

```

---

