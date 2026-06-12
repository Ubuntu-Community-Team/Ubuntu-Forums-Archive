---
title: "what is __init__ in Python? and what are classes and objects as opposed to functions?"
date: 2007-09-01
forum: Programming Talk
---

### Post by yuvlevental on 2007-09-01
Sorry for asking a noobish question but what is __init__? and what are classes and objects?

Thanks,
yuvlevental

---

### Post by oOJINxOo on 2007-09-01
no worries about the n00bish question, but sorry about this answer, if your new to python, and are starting to learn about oop, you really need to be reading tutorials on this...

__init__ is a kind of constructor, when a instance of a class is created, 
python calls __init__() during the instantiation to define additional behavior that should occur when a class is instantiated, basically setting up some beginning values for that object or running a routine required on instantiation.

you'll need to learn about classes at your own pace, afew sources for learning i'd recommend is:

#The main documention for python
[http://www.python.org/doc/current/tut/node11.html](http://www.python.org/doc/current/tut/node11.html)

#and if you can afford (or find *whistles innocently*) this amazingbook by Wesley chun:
Core Python Programming 2nd Edition, by Wesley J Chun
[http://www.amazon.com/Core-Python-Programming-2nd/dp/0132269937/ref=pd_bbs_sr_1/102-3375149-8705702?ie=UTF8&s=books&qid=1188673651&sr=8-1C](http://www.amazon.com/Core-Python-Programming-2nd/dp/0132269937/ref=pd_bbs_sr_1/102-3375149-8705702?ie=UTF8&s=books&qid=1188673651&sr=8-1C)

who ate my .py !?!?!

---

### Post by triptoe on 2007-09-01
> **yuvlevental said:**
> Sorry for asking a noobish question but what is __init__? and what are classes and objects?

Thanks,
yuvlevental

init is an abbreviation for initialization. 

For instance if I have a Point class... that has two objects which are the x and y coordinates i can do this:

```

class Point():
     pass

point = Point()
point.x = 3.0
point.y = 4.0

```

so instead you can do this:

```

class Point():
     def __init__(self, x=0,y=0):
           self.x = x
          self.y = y

```

now you can make a point like this:

point = Point(3,4)

or 

point = Point()  # which gives you a point of default 0,0 .

---

### Post by Wybiral on 2007-09-01
```

class HelloWorld:
    def __init__(self):
        self.outText = "Hello World"
    def printOut(self):
        print self.outText

myHelloWorld = HelloWorld()
myHelloWorld.printOut()

```

When the object instance "myHelloWorld" of object type "HelloWorld" is initialized (where "myHelloWorld" is assigned as type "HelloWorld") the initializer is called, in this case setting "self.outText" to "Hello World".

If you've ever used C++, it's a constructor. You use it to create the initial conditions that the object should have (default values and such).

It can also take parameters after "self" like any other function.

---

### Post by pmasiar on 2007-09-01
> **yuvlevental said:**
> Sorry for asking a noobish question but what is __init__? and what are classes and objects?

classes and objects are a way how to bundle together data (objects properties or attributes) and programs (objec't methods), so you will use proper methods with each bunch of data. It is kind of namespace in a way.

Class is like a cookie-cutter: every time you use it, it will create cookie for you. All will be different (from different material), but still like each other: they will have some individual data you specify at creation, and common behavior - they all use methods (functions) defined by the class. This is all you need to know to **use** existing objects.

But in Python, you don't have to define your own objects until you need it, you can easily program old-style procedural code and not worry about OOP.

You can easily have (list of) dictionaries, and use them almost like objects. Learn procedural programming first, we lived without OOP for 30 years without (much) problems, so you can wait 3 months :-)

__init__ is example of special method used when defining your own classes. Ie if you define __add__() for object x,  Python will try to use it for x + y. There is many of those special methods or function names, all with prefix __ (double-under).

---

### Post by slavik on 2007-09-01
contructor = function called after memory for the object has been allocated. Usually used to set "default" values.

---

### Post by yuvlevental on 2007-09-01
so, let me get this straight...
A class is a kind of object that can hold other objects,  which are things that do stuff.

```

class Printer:
	def print_something (self, what):
		print "This object says", what
printobj = Printer ()
printobj.print_something ("Hello there")

```

the class is Printer. then there is def print_something (self, what): which defines the function print_something with (self, what). Does "self" stand for printobj, and does "what" stand for the input of the function "Hello There?"  And printobj is an object. And __init__ is for automatically generating new objects
```

class Person:
	def __init__(self, name):
		self.name = name
	def sayHi(self):
		print 'Hello, my name is', self.name

p = Person('Swaroop')
p.sayHi()

```
Like the object "p" is generated here.

Am i correct in my assumptions, and is this the hardest part of Python? Also, what is the point of the __init__ method and classes

Thanks,
Yuvlevental

---

### Post by yuvlevental on 2007-09-01
and does OOP mean that there are infinite possibilities w/parameters wheres POP mean that there are a certain number of possibilities with infinite parameters for these possibilities? And is __main__ the python module itself?

Thanks, Yuvlevental

---

### Post by pmasiar on 2007-09-01
> **yuvlevental said:**
> so, let me get this straight...
A class is a kind of object that can hold other objects, 

Wrong. Class is way to create objects (cookie-cutter), not the cookie. Cookie is object instance, you can do something with it. Class is good only for creating objects of given type.

> 
Does "self" stand for printobj, and does "what" stand for the input of the function "Hello There?"  

yes and yes.

> 

And printobj is an object. And __init__ is for automatically generating new objects
```

class Person:
	def __init__(self, name):
		self.name = name
	def sayHi(self):
		print 'Hello, my name is', self.name

p = Person('Swaroop')
p.sayHi()

```
Like the object "p" is generated here.



Yes. It is not rocket science, is it?

> 
Am i correct in my assumptions, and is this the hardest part of Python? Also, what is the point of the __init__ method and classes


no (IMHO) - OOP is just another way to try to tame the complexity


__init__ was explained above. Did you missed it?

---

### Post by nanotube on 2007-09-01
oop = "object oriented programming"
pop = "post office protocol" :) (though in this context may refer to "procedure oriented programming"? usually it's just called 'procedural programming', though. never seen it acronymed as "pop")...

---

### Post by yuvlevental on 2007-09-01
its procedure oriented programming

---

### Post by pmasiar on 2007-09-02
I was surprised that it even exists, but [http://www.google.com/search?q=%22procedure+oriented+programming%22](http://www.google.com/search?q=%22procedure+oriented+programming%22) has 656 hits :-)

---

### Post by xtacocorex on 2007-09-02
Procedural should definitely not be put into an acronym, it offends (at least me) those of us who still relish the methods. :) [This is a joke, if you don't get it]

Pretty much, classes are ways to create objects; objects are data types with built in methods.  

__init__ is a way to specify default values when you declare an object; the values are set in the class definition.

__main__ is where the Python interpreter denotes the start of actual code, not including function and class definitions.

---

### Post by scphan on 2009-03-09
procedure oriented programming is based on the defining of functions which each has a job to do, and the functions together form the basis of the program, you can use python for 'pop' by only using function definitions, object-oriented programming is where you can organize specific functions that are similar or work together into a class like a noun (object) which has certain actions/verbs it can perform (functions/methods). The class can not only hold specific functions/methods but also hold its own attributes(data members/variables with values) which are supposedly only visible to its inner parts (its functions/methods) which is termed data encapsulation in OOP programming, what makes OOP programming so useful is that its classes are isolated from other classes and only interact through function/method calls making modification of the program easy by not having to go and change everything in all of the methods to make it compatible with your updates, say you make two classes, one for computing trig. functions and another for computing inv. functions, if you were to make an error in one of them and you know the other one works just fine then your changes are isolated to only the class that needs the fix, kinda like taking out a broken module from the system and fixing it then plugging it back in without touching any other parts of system

object are instantiated(a unique copy is created in memory) as needed by the user and each time they are instantiated their constructors are called, these constructors initialize any of the object's own variables before they are used by any methods, to initialize the object's variables before they're used is good OOP practice since it prevents the dependence of the programmer on the user to know how to initialize the variables before they're used thus preventing possible errors

here some Java code for OOP:

public class SomeClass
{
    int var1;
    String string1;
    
    // no parameter constructor
    public SomeClass()
    {
        var1 = 12345;
        string1 = "Let assign this string before any methods use this variable";
    }

    public int getVar1()
    {
        return var1;
    }
   
    public String getString1()
    {
         return string1;
    }
}



and the equivalent in python:

class SomeClass:
     """documentation string (optional)"""
     
     def __init__( self ):
           self.var1 = 12345
           self.string1 = "Lets assign this string before any method uses it"

     def getVar1( self ):
           return self.var1

     def getString1( self ):
           return self.string1

# end of class declaration

all methods including constructors must specify at least one parameter, that one parameter is the object reference which allow the methods of the class to access its own variable and other methods of its own.  By convention this parameter/argument is named 'self', it isn't specific when you call the object ( class = SomeClass(), class.getVar1(), class.getString1() ) but when you define the class you have to specify it

---

