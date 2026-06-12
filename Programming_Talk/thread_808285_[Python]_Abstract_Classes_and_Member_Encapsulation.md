---
title: "[Python] Abstract Classes and Member Encapsulation"
date: 2008-05-26
forum: Programming Talk
---

### Post by dwhitney67 on 2008-05-26
I am fairly new to the Python programming language, having only taught myself the basics from the on-line tutorials.  I really should get a book!

Anyhow, I have read that there is no such thing as an abstract class in Python.  Ok... so therefore how do I go about preventing an "non-real" object from being instantiated?

For instance, with this snippet of code:
[PHP]#!/usr/bin/python

import math
import sys

##
## Shape (dimensionless)
##
class Shape:
	# I would like to prevent this class from being directly
	# instantiated because it does not represent a real object.
	# How can I do this???
	def __init__( self, shapeType ):
		self.shapeType = shapeType
		self.__abstract__ = "Do not permit instantiation of a Shape!"

	def getType( self ):
		return self.shapeType

	# This method should be abstract; not return a value!
	def calculateArea( self ):
		return 0



##
## Circle
##
class Circle( Shape ):
	def __init__( self, radius ):
		Shape.__init__( self, "Circle" )
		self.radius = radius
		Shape.__abstract__ = 10    # What?  Allowed!!!

	def calculateArea( self ):
		return math.pi * self.radius * self.radius


##
## Main Program
##
try:
	circle = Circle( 3.0 )
	print "Shape type = ", circle.getType()
	print "Shape area = ", circle.calculateArea()
	print ""

	# I want to prevent this!  How???
	shape = Shape( "Bogus" )
	print "Shape type = ", shape.getType()
	print "Shape area = ", shape.calculateArea()
	print ""

except:
	print "Exception Caught:", sys.exc_info()[1][/PHP]

The other question I have is how to enforce data-typing?  I find it somewhat disturbing (perhaps laughable) that a class can define a local variable type, and a sub-class can change the type's value to some other data type (e.g. from a string to an integer).

Does Python not provide the tools necessary to define variables and methods as private or protected attributes of a class, thus guarding them from accidental overwriting/redefining?

---

### Post by CptPicard on 2008-05-26
Python doesn't do things like that... the whole object system is much looser in a lot of ways than the bondage and discipline stuff of statically typed OOP languages like Java or C++.

I'm not a huge Python expert but I was wondering about the same things... but they are not really necessary. You just need to realize that "programmers are consenting adults" as pmasiar says -- that is, yeah, there is no really private data. A Python object is essentially a group of stuff in RAM that you can manipulate pretty much at will, and tack methods on for nice OOP-style syntactic sugar when you call them on that particular instantiation of group of stuff in RAM.

Now, there are no abstract classes because in Python, the idea of duck typing and "protocols" take their place. If some object has some particular method that fulfills some particular protocol -- an agreed-upon behaviour -- then it just automagically "is of that interface" in Java terms. Python's standard generic methods make heavy use of this idea... I was a bit put off originally for example by len() being a Python API function instead of some abstract interface method,  but ... the whole point is that len() calls __len__() on an object. Define that, and the generic method len() works magically.

Of course because duck typing is the behavioural-interface-abstraction of choice, of course stuff like inheritance loses some significance... it's there in Python, but things like type hierarchies and resulting polymorphism simply aren't as important anymore.

---

### Post by LaRoza on 2008-05-26
> **CptPicard said:**
> Python doesn't do things like that... the whole object system is much looser in a lot of ways than the bondage and discipline stuff of statically typed OOP languages like Java or C++.

I'm not a huge Python expert but I was wondering about the same things... but they are not really necessary. You just need to realize that "programmers are consenting adults" as pmasiar says -- that is, yeah, there is no really private data. A Python object is essentially a group of stuff in RAM that you can manipulate pretty much at will, and tack methods on for nice OOP-style syntactic sugar when you call them on that particular instantiation of group of stuff in RAM.


Well, "private" is as "private" does: [http://docs.python.org/tut/node11.html#SECTION0011600000000000000000](http://docs.python.org/tut/node11.html#SECTION0011600000000000000000)

---

### Post by dwhitney67 on 2008-05-26
It seems then that one should merely provide documentation to specify a class is considered "abstract", and also document which methods should be re-implemented by subclasses.  Another tool at one's disposal is to raise an exception in these abstract methods (see below).

As for hoping all programmers behave as "adults", that's a pipe dream.  I have seen many that behave as "children"... and dumb ones at that.

LaRoza, "private" date members, if they exist, don't seem to be that private if a subclass can alter its value.  I'm not sure if you were attempting to say this or not; I had previously come across that same webpage you posted, but found it of little help.

Anyhow, here's an update for my Shape class:
[PHP]class Shape:
        __abstract__  = "Shape is an abstract class!"

        def __init__( self, shapeType ):
                self.shapeType = shapeType

        def getType( self ):
                return self.shapeType

        def calculateArea( self ):
                raise Exception( self.__abstract__ )[/PHP]

---

### Post by CptPicard on 2008-05-26
> **dwhitney67 said:**
> It seems then that one should merely provide documentation to specify a class is considered "abstract", and also document which methods should be re-implemented by subclasses.  Another tool at one's disposal is to raise an exception in these abstract methods (see below).


An even more pythonic way as far as I understand the zen of Python is to just ... not define that "abstract class" at all, but just document the behaviour you expect from a Shape. If it acts as a shape in some particular context, it is a shape. Your abstract do-nothing Shape class is just added baggage that is meaningless in the Python context.

I can't remember off the top of my head what the exception is that Python throws when a method is not found on an object, but you can eliminate your own exception throwing simply by trying calling your shape methods on *any* object and then just handling the Python's built-in error that gets thrown when it's not a shape you're trying to use as a shape. The end result is the same.

Another way to do this is to specifically check in advance with "has_attr" if your object will be able to be called the way you expect.

A Python class is really nothing but a sort of preconfiguration function, and that makes Python's object system interesting. Anything you can do in "class" can, according to my understanding, be done in code at runtime on some "null object" that you'd just build.

---

### Post by Quikee on 2008-05-26
NotImplementedError should be the right exception for abstract classes. The documentation says: > This exception is derived from RuntimeError. In user defined base classes, **abstract methods should raise this exception when they require derived classes to override the method.** New in version 1.5.2. 

As a side note: SmallTalk - as one of the first object oriented languages does not have abstract classes (if I'm not mistaken Simula also does not have them) or any "access" restrictors - every message (method) is "public", every instance variable is "private".

---

### Post by LaRoza on 2008-05-26
> **dwhitney67 said:**
> 
LaRoza, "private" date members, if they exist, don't seem to be that private if a subclass can alter its value.  I'm not sure if you were attempting to say this or not; I had previously come across that same webpage you posted, but found it of little help.


I know. I was saying that private members are private not because it is enforced, but because the programmer codes them that way.

---

### Post by pmasiar on 2008-05-27
> **dwhitney67 said:**
> As for hoping all programmers behave as "adults", that's a pipe dream.  I have seen many that behave as "children"... and dumb ones at that.

That's not a problem - or not a technical problem, so it cannot have technical solution. Social problems have social solutions: "don't use modules by people who do not accept commonsense rules". This will not prevent you to change something in classes, if you really need to, and you really know what you are doing. In any case, you have the sources, right? :-) You can always "#define private public" and be done with any protection :-)

Goal is to make life easier for responsible  programmer. If some coder is not responsible enough to follow guidelines, solution is not to use language which forces him to do so (forcing contortions to whole team), but to fire the offender :-)

> LaRoza, "private" date members, if they exist, don't seem to be that private if a subclass can alter its value.  

By custom, variable name starting with _ is considered "private". Variable starting with __ (double _) is subject to name mangling by adding class name (but you still can access it if you need to - gives you enough rope to hang yourself, if you want to).

As Larry Wall famously said, if I ask you that variable is my private, you should be nice person and accept it. Let's agree you will not make fire in my living room because I asked you to stay out, not because I have a shotgun. This is what is meant "consenting adults": It is like having driving license: of course you can drive in left line, but you will not, so cars going 100km/h in opposite directions can miss each other by 1 meter.

Some subset of what you may want from abstract classes will be added in Py3.0: read links to discussion at [http://www.dougma.com/archives/date/2007/06/](http://www.dougma.com/archives/date/2007/06/) and especially Guido's [Python 3000 Status Update](http://www.artima.com/weblogs/viewpost.jsp?thread=208549) comments about Changes to the Class and Type System: something like Java's interfaces, and decorator to mark a method as in need of implementing. IMHO this is more flexible: it lets you provide default implementation of some methods if it makes sense, without creating ravioli code (to many classes containing other classes, like Java does)

---

