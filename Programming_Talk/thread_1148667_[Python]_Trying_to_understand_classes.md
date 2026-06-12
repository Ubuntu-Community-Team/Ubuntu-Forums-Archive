---
title: "[Python] Trying to understand classes"
date: 2009-05-04
forum: Programming Talk
---

### Post by dodle on 2009-05-04
I am still struggling with creating and understanding classes.  I wrote a snippet to try and help me but can't figure out what is wrong.  If someone could point out my mistakes I would be very greatful.

[php]#! /usr/bin/env python
"""
Testing classes
"""

x = 0
y = 0
pos = "%s,%s" % (x,y)

class Character():
	def walkNorth():
		y += 1
	
	def walkSouth():
		y -= 1
	
	def walkEast():
		x += 1
	
	def walkWest():
		x -= 1

Me = Character()

loop = True
while loop:
	print "You are at %s" % pos
	dir = raw_input("Which direction?: ").lower()
	if dir == "n":
		Me.walkNorth()
	elif dir == "s":
		Me.walkSouth()
	elif dir == "e":
		Me.walkEast()
	elif dir == "w":
		Me.walkWest()[/php]

---

### Post by melopsittacus on 2009-05-04
If I am not mistaken, you need to have a self parameter in each method declaration, so try something like this:


```
x = 0
y = 0
pos = "%s,%s" % (x,y)

class Character():
    def walkNorth(self):
        y += 1
    
    def walkSouth(self):
        y -= 1
    
    def walkEast(self):
        x += 1
    
    def walkWest(self):
        x -= 1

Me = Character()

loop = True
while loop:
    print "You are at %s" % pos
    dir = raw_input("Which direction?: ").lower()
    if dir == "n":
        Me.walkNorth()
    elif dir == "s":
        Me.walkSouth()
    elif dir == "e":
        Me.walkEast()
    elif dir == "w":
        Me.walkWest()  
```

self is actually the equivalent of this in c++


edit: Another thing: x and y should be made member variables somehow, because in this way they always remain set to zero.

---

### Post by Can+~ on 2009-05-04
This is clearly a misunderstanding of the idea of "scopes".

Every variable you define inside a function, is "local" (it can't be seen from outside) to that function, unless specified otherwise ([FONT="Courier New"][COLOR="DeepSkyBlue"]global[/COLOR][/FONT] keyword). Same goes for variables defined inside a class. Globals are seen by everyone.

The thing is that you defined x and y on the "global" scope, where everyone can see them.

Now that you understand this idea, let's put it this way:

```
global variables

def myFunction():
    variables local to my function

class MyClass:
    variables local to MyClass

    def myMethod():
        variables local to myMethod
```

This is mainly for a property called "encapsulation", where you don't want to data get mixed into spaghetti code (which leads to impossible to debug/understand code).

To interact between the different levels, or scopes, you use special operators, for example, your average

```
myInstance.myMethod()
```

Calls the method defined inside myInstance (differnt scope).

But how do you do it inside a class? [FONT="Courier New"][COLOR="DeepSkyBlue"]self[/COLOR][/FONT]

[PHP]def MyClass:
    attribute = 0

    def myMethod(self):
        self.attribute += 1[/PHP]

[FONT="Courier New"][COLOR="DeepSkyBlue"]self[/COLOR][/FONT] is a reference to the scope of the class (pointer for C/C++ programmers) and with it you can access the scope defined on your class.

---

### Post by dodle on 2009-05-04
Thank you very much.  Here is what I came up with:

[php]"""
Testing classes
"""

x = 0
y = 0

class Character():
	def walkNorth(self, x, y):
		y += 1
		return y
	
	def walkSouth(self, x, y):
		y -= 1
		return y
	
	def walkEast(self, x, y):
		x += 1
		return x
	
	def walkWest(self, x, y):
		x -= 1
		return x

Me = Character()

loop = True
while loop:
	pos = "%s,%s" % (x,y)
	print "You are at %s" % pos
	dir = raw_input("Which direction?: ").lower()
	if dir == "n":
		y = Me.walkNorth(x, y)
	elif dir == "s":
		y = Me.walkSouth(x, y)
	elif dir == "e":
		x = Me.walkEast(x, y)
	elif dir == "w":
		x = Me.walkWest(x, y)
[/php]

---

### Post by Can+~ on 2009-05-04
> **dodle said:**
> Thank you very much.  Here is what I came up with:

You still don't grasp the idea.

This is how it should look like

[PHP]#!/usr/bin/python

"""
Testing classes
"""

#x = 0 <-- NO!
#y = 0

class Character():
	# Class scope
	x = 0
	y = 0
	
	def walkNorth(self):
		#Using self to access the class scope
		self.y += 1
	
	def walkSouth(self):
		self.y -= 1
	
	def walkEast(self):
		self.x += 1
	
	def walkWest(self):
		self.x -= 1
	
	def getPos(self):
		return (self.x, self.y)

me = Character()

loop = True
while loop:
	print "You are at (%d, %d)" % me.getPos()
	
	dir = raw_input("Which direction? (q:quit): ").lower()
	
	if dir == "n":
		me.walkNorth()
	elif dir == "s":
		me.walkSouth()
	elif dir == "e":
		me.walkEast()
	elif dir == "w":
		me.walkWest()
	
	elif dir == "q":
		loop = False
[/PHP]

---

### Post by benj1 on 2009-05-04
hmm i alway thought the correct/recommended way was

```
#!/usr/bin/python

"""
Testing classes
"""

#x = 0 <-- NO!
#y = 0

class Character():
    # Class scope
    def __init__(self, x=0, y=0):
    	self.x = x
    	self.y = y
    #x = 0
    #y = 0
    
    def walkNorth(self):
        #Using self to access the class scope
        self.y += 1
    
    def walkSouth(self):
        self.y -= 1
    
    def walkEast(self):
        self.x += 1
    
    def walkWest(self):
        self.x -= 1
    
    def getPos(self):
        return (self.x, self.y)

me = Character()

loop = True
while loop:
    print "You are at (%d, %d)" % me.getPos()
    
    dir = raw_input("Which direction? (q:quit): ").lower()
    
    if dir == "n":
        me.walkNorth()
    elif dir == "s":
        me.walkSouth()
    elif dir == "e":
        me.walkEast()
    elif dir == "w":
        me.walkWest()
    
    elif dir == "q":
        loop = False 
``` 

or is this just for reasons of being able to modify defaults?

---

### Post by days_of_ruin on 2009-05-04
Or you can add a constructor method.
[PHP]#!/usr/bin/python

"""
Testing classes
"""

#x = 0 <-- NO!
#y = 0

class Character(object):

	
        def __init__(self):
            self.x = 0
	    self.y = 0
	
	def walkNorth(self):
		#Using self to access the class scope
		self.y += 1
	
	def walkSouth(self):
		self.y -= 1
	
	def walkEast(self):
		self.x += 1
	
	def walkWest(self):
		self.x -= 1
	
	def getPos(self):
		return (self.x, self.y)

me = Character()

loop = True
while loop:
	print "You are at (%d, %d)" % me.getPos()
	
	dir = raw_input("Which direction? (q:quit): ").lower()
	
	if dir == "n":
		me.walkNorth()
	elif dir == "s":
		me.walkSouth()
	elif dir == "e":
		me.walkEast()
	elif dir == "w":
		me.walkWest()
	
	elif dir == "q":
		loop = False
[/PHP]

Also note that you should always make your class inherit from something.
Inherit from ```
object
``` if you don't have anything you want to inherit from.

---

### Post by Can+~ on 2009-05-04
> **benj1 said:**
> hmm i alway thought the correct/recommended way was

or is this just for reasons of being able to modify defaults?

Constructors usually exist when you need to specifiy how the object will be, the instance could be set to start at an (x,y) and then a constructor would make sense.

I omitted it for simplicity, didn't want to complicate the OP with more concepts.

---

### Post by dandaman0061 on 2009-05-04
I would also suggest putting the 'x' and 'y' in the constructor __init__ method.  Putting them in the class scope makes them common to all instances of that class.  Putting them in the constructor/__init__ method will make them unique per instance of that class.

Class Scope:
```

class Character(object):
    x = 0
    y = 0

```
Instance Scope:
```

class Character(object):
    def __init__(self):
        self.x = 0
        self.y = 0

```

And skimming the rest of your code, it looks like the x and y attrs are meant to be unique to each instance of type 'Character'.

Think of it this way... you want each Character to have their own position, so they all need to have their own x and y.  But say you wanted all of your Characters to have two legs, and you had another class 'Dog' where all instances of 'Dog' had 4 legs.  These class/static attributes should be defined in the class scope.

e.g.
```

class Character(object):
    num_legs = 2
    def __init__(self):
        # define instance attrs here
        self.x = 0
        self.y = 0
        self.name = "no name"
        self.mood = "happy"
        # etc...

class Dog(object):
    num_legs = 4
    def __init__(self):
        self.x = 0
        self.y = 0
        self.color = "black"

```

You still refer to the class/static attributes the same as you would instance attributes (e.g. self.num_legs) BUT you can also refer to them using the class e.g. (Character.num_legs or Dog.num_legs)

---

### Post by dodle on 2009-05-04
> **Can+~ said:**
> You still don't grasp the idea.

Sorry, I hadn't refreshed my browser.  I was responding to melopsittacus.

---

