---
title: "Python beginner help plz"
date: 2007-05-10
forum: Programming Talk
---

### Post by microsoft92sucks on 2007-05-10
I just started Python and im reading a how to ( [http://hetland.org/writing/instant-hacking.html](http://hetland.org/writing/instant-hacking.html) ) and im trying to get this coding to work and it seems to be working fine except it wont let me put in 1 or 2 to chose wat i want circle or triangle wat the coding does is calculate the area of a circle or triangle y cant i get it to take the input and calculet it heres the coding
print "welcome"
print "chose 1=tri 2=cir"
shape=input(">")
if shape == 1:
    height = input()
    width = input()
    area = input()
    print "area=", area
else:
    radius = input()
    area = 3.14*(radius**2)
    print "area2=", area

Im using SPE but i tried it in DrPython and IDLE
please help i really want to proggram

Another ? - the mark how do i get to Pygame i already installed it but its not under proggraming or any thing please help

---

### Post by Siph0n on 2007-05-10
hey, i forget the EXACT syntax, but its something like : shape = input("Choose 1 for triangle, 2 for circle")
Also, python is based off of indentation, so make sure u have your if and else stuff indented. Anytime you want to get input just pick a name of the input, like radius, and make it equal to input("What is the radius").

```
print "welcome"
shape = input("choose 1=tri 2=cir")
if shape == 1:
   height = input("height: ")
   width = input("width: ")
   area = input("area: ")
   print "area=", area
else:
   radius = input("radius: ")
   area = 3.14*(radius**2)
   print "area2=", area

```

I don't have python installed here, so I can't test it out... but try that :)

---

### Post by xtacocorex on 2007-05-10
Using [ code ]  [ /code ] (without the spaces) will make your code easier to read in a post.  It might also help if you used proper English and not shortened words, it'd be easier to understand what you are trying to ask.

Here is my version of what you typed and it works (with the exception of the second input for the triangle)
```

print "welcome"
print "choose 1=tri 2=cir"

shape=input(">")
if shape == 1:
        height=input("h:")
        base=input("b:")
        area = (1/2.)*base*height
else:
        radius=input("r")
        area = 3.14*radius*radius

print "area = ", area


```

---

### Post by microsoft92sucks on 2007-05-10
its saying print welcome choose 1=tri 2=cir but it wont let me put in 1 or 2. y not?

---

### Post by Siph0n on 2007-05-10
did u try my code above??? :) cause just printing to the screen wont let u input values :)

---

### Post by Siph0n on 2007-05-10
oops.... lol take out this line :)   area = input("area: ")  lol you shouldn't ask for the area, thats what the program is suppose to to lol... and I tested it and it works...

```
print "Welcome"
shape = input("choose 1=triangle or 2=circle: ")
if shape == 1:
   height = input("height: ")
   width = input("width: ")
   print "area=", area
else:
   radius = input("radius: ")
   area = 3.14*(radius**2)
   print "area2=", area
```

---

### Post by Tenicus on 2007-05-10
```

shape = raw_input("choose 1=triangle, 2=circle")
if shape == "1":
    height = int(raw_input("Height:"))
    width = int(raw_input("Width:"))
    area =  height * width /2
    print "area=", area
elif shape == "2":           #I did this in case the user entered 3 or higher
    radius = int(raw_input("Enter radius"))
    area = 3.14*(radius**2)
    print "area2=", area

```

---

### Post by n0dl on 2007-05-10
By the way i suggest you use raw_input and cast it as an integer type versus using input. A malicious user can enter a command via input.

---

### Post by Siph0n on 2007-05-10
awesome thx for the tip!!! :) I haven't used python in almost a year :)

---

