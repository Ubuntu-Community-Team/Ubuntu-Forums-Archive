---
title: "how to deal with global variables in python ?"
date: 2006-02-28
forum: Programming Talk
---

### Post by krypto_wizard on 2006-02-28
Hi,

I have three python classes and a fourth file which reads input and has lots of variables. These variables are needed to do some computations in all three classes some or the other time.

How can I structure my program so that I avoid making the variables read from file as global and still do all the importing among different modules without problems.

I had some problems with cross import modules where first.py calls some varible of second.py and second.py calls some varaible of first.py.

Could you give me some hints as to how can I arrange my above mentioned code in classes such that I dont land into cross import module errors.

Thanks

---

### Post by thumper on 2006-02-28
My suggestion is to use a single module - and don't use global variables.

Have a class that encapsulates the "global" variables and pass an instance of that class into the constructors of the other three.  These other classes can then reference the file_reader class as and when needed.

There is a pattern called "paramatise from above" which describes this.  

It would then look something like this:
```

class A(object):
   def __init__(self, config):
      self.config = config
   def some_func(self):
      # do something with config

# ditto for class B and C

class Config(object):
   def __init__(self, params):
      # load info, do whatever

if __name__ == "__main__":
   # construct the config
   config = Config(some params)
   a = A(config)
   b = B(config)
   # et al
   # do stuff with a,b,c and config...

```

---

### Post by WelterPelter on 2006-02-28
Thumper's reply is the object-oriented version and the one that -- in my very limited experience -- works best. Create an object that holds the data you want and pass the object around. Handy.

---

### Post by krypto_wizard on 2006-02-28
Thanks Tim, I like your aproach!!! 

I am modifying my code as per your sugestion. Thanks once again.

A quick question again. There are some vaiables which change over the course of the program like system_time, number_of_nodes etc.
My main.py update it after every iteration but the other classes also needs those variables. How should I handle them. Should I pass those variables thru function parameters or there is some other way for this.

[QUOTE=thumper]My suggestion is to use a single module - and don't use global variables.

Have a class that encapsulates the "global" variables and pass an instance of that class into the constructors of the other three.  These other classes can then reference the file_reader class as and when needed.

There is a pattern called "paramatise from above" which describes this.  

It would then look something like this:
```

class A(object):
   def __init__(self, config):
      self.config = config
   def some_func(self):
      # do something with config

# ditto for class B and C

class Config(object):
   def __init__(self, params):
      # load info, do whatever

if __name__ == "__main__":
   # construct the config
   config = Config(some params)
   a = A(config)
   b = B(config)
   # et al
   # do stuff with a,b,c and config...

```[/QUOTE]

---

### Post by thumper on 2006-02-28
Well if you have passed a reference to a config object into the other objects that use them, then updating the variables in the config object will be visible in the objects that contain references to it.

However if you rebind the config object to a different instance of the Config class then they won't be visible as the other objects have a reference to the old instance.

So... have some update method on the config class to update itself.

---

### Post by krypto_wizard on 2006-02-28
I am passing the object. I will show you how I do it.

```

## filereader.py
class filereader:
    def __init(self, filename):
         ## Does reading of files

## main.py
def main():
    f = filereader(input.txt)
    a = class_A(f)
    b = class_B(f)
    ## Other code

## 
class class_A:
    def _init(self, file):
         self.file = file
    ## Other code

## ditto for class_B

```

So essentially, I am pasing the object created in main to other classes.
Is it what you wanted ? Since I a not passing reference here so I was kinda confused. (haven't really dealt with pointers or references in python as yet).

Your comments are welcome.

Thanks


[QUOTE=thumper]Well if you have passed a reference to a config object into the other objects that use them, then updating the variables in the config object will be visible in the objects that contain references to it.

However if you rebind the config object to a different instance of the Config class then they won't be visible as the other objects have a reference to the old instance.

So... have some update method on the config class to update itself.[/QUOTE]

---

### Post by thumper on 2006-02-28
Python is a little similar to Java in that when assigning an object it is a reference to an object (don't think about C++ references these are different).

Also you are doing old style classes.  You want your classes to be new style ones, so inherit from object like shown below.  There are many sometimes suttle differences between old style and new style classes in python that I'm not going to go into here.

What I'd do for the filereader would be something like:

```
class filereader(object):
    def __init(self, filename):
        self.filename = filename
        self.read_file()

    def read_file(self):
        # do the reading


```That way the filereader can be updated by calling read_file().

---

### Post by krypto_wizard on 2006-02-28
A dumb question (forgive me..i am a newbie)

what do u mean by object in "class filereader(object)" ? What exactly are you trying to say by inheriting object ?

Do you mean other classes will inherit filereader class ?

I am really sorry for such dumb questions.

I am trying to learn Object Oriented Programming alongwith python.

Thanks for all your help,



[QUOTE=thumper]Python is a little similar to Java in that when assigning an object it is a reference to an object (don't think about C++ references these are different).

Also you are doing old style classes.  You want your classes to be new style ones, so inherit from object like shown below.  There are many sometimes suttle differences between old style and new style classes in python that I'm not going to go into here.

What I'd do for the filereader would be something like:

```
class filereader(object):
    def __init(self, filename):
        self.filename = filename
        self.read_file()

    def read_file(self):
        # do the reading


```That way the filereader can be updated by calling read_file().[/QUOTE]

---

### Post by thumper on 2006-02-28
Inheritance in python is shown by the superclass being in brackets after the name of the class:
```
class filereader(object):
```
Says that the class filereader inherits from object.  The base object class has some functionality that you don't get with the old style classes which is what you get if the brackets are omitted.

Other classes could inherit from filereader if that is what you want (it almost never is).  Inheritance solves one type of problem, and the trick is being able to identify that problem and not try to use inheritance to solve problems that are best solved with agregation or simple parameters.

---

### Post by WelterPelter on 2006-02-28
class anything(object): is just the new way to write classes (that don't inherit from any other type of object). Do it that way.

---

### Post by krypto_wizard on 2006-02-28
is filereader inhering from any object ? If yes, which object is that ?

I understood your explaination on inheritance, but i also think that having filereader as super class is not a good idea here as it will create different copies of the same stuff.



[QUOTE=thumper]Inheritance in python is shown by the superclass being in brackets after the name of the class:
```
class filereader(object):
```
Says that the class filereader inherits from object.  The base object class has some functionality that you don't get with the old style classes which is what you get if the brackets are omitted.

Other classes could inherit from filereader if that is what you want (it almost never is).  Inheritance solves one type of problem, and the trick is being able to identify that problem and not try to use inheritance to solve problems that are best solved with agregation or simple parameters.[/QUOTE]

---

### Post by LordHunter317 on 2006-02-28
Why is this variable even global and not owned by a method?

It's ok to have main have variables in it's scope, you know.

Generally, any method to create globals, even if you wrap them in a class, is a hack.  Thumper's method puts you on the right track, but it still means you have too much scaffolding.

What irks me more is setups that encourage this silly behavior (VS.NET 2K5, I'm looking at you)

---

### Post by krypto_wizard on 2006-02-28
what should I do ??

[QUOTE=LordHunter317]Why is this variable even global and not owned by a method?

It's ok to have main have variables in it's scope, you know.

Generally, any method to create globals, even if you wrap them in a class, is a hack.  Thumper's method puts you on the right track, but it still means you have too much scaffolding.

What irks me more is setups that encourage this silly behavior (VS.NET 2K5, I'm looking at you)[/QUOTE]

---

### Post by LordHunter317 on 2006-03-01
Well actually, I suppose I owe thumper an apology, as I think I misread the path he was trying to lead you down eariler.  For that, I apologize.

What code you've posted looks ok, but does the class need to be able to read files all the time?  Better might be to create a factory method: this takes a file reader and returns a new instance of the object, read from a file.

I mention this simply because the case where you only want to create an object from a file are in practice, pretty low.  At anyrate, it's generally good future-proofing to assume you will want to create objects in other manners, even if it is true now.  

So, your objects should only take what information they need to be instantiated (in C++ because I'm too tired to do in Python):```
class A {
   int foo_; 
   int bar_;

public:
    A(foo, bar) : foo_(foo), bar_(bar)
   { }
};

A create_A_from_file(std::istream& file)
{
   int foo, bar;
   istream >> foo >> bar;
   return A(foo, bar);
}
```Is how'd I do it in C++.  This yields both more flexibility and more encapsulation.

create_A_from_file could also be a static method, in this example, in C++, anyway.  In Java or C#, it'd have to be.

---

### Post by thumper on 2006-03-01
[QUOTE=krypto_wizard]is filereader inhering from any object ? If yes, which object is that ?[/QUOTE]
filereader is inheriting from the **class** object.  The terminology is a little confusing, but that's the way it works.

[QUOTE=krypto_wizard]I understood your explaination on inheritance, but i also think that having filereader as super class is not a good idea here as it will create different copies of the same stuff.[/QUOTE]
Any class is potentially a super class.  I'm not sure what you mean by having different copies of the same stuff.

**LordHunter317** typo in your sample code - streaming in from istream not file.  Also I think that **krypto_wizard**'s two or three classes aren't being constructed from the contents of the *Config* class, but they store a reference to it and use values from it in other methods.

---

### Post by LordHunter317 on 2006-03-01
[QUOTE=thumper]**LordHunter317** typo in your sample code - streaming in from istream not file.[/quote]That was intentional.  I said file, but I wrote 'any stream' because in C++ it's sensless to take an ifstream instead of an istream.

If this were other languages, maybe not.

---

### Post by krypto_wizard on 2006-03-01
when do we use the keyword "global" in python ? How can we use it ?

---

### Post by thumper on 2006-03-01
[QUOTE=LordHunter317]That was intentional.  I said file, but I wrote 'any stream' because in C++ it's sensless to take an ifstream instead of an istream.

If this were other languages, maybe not.[/QUOTE]
Think you missed the point.
```
A create_A_from_file(std::istream& file)
{
   int foo, bar;
   istream >> foo >> bar;
   return A(foo, bar);
}
```
should be
```
A create_A_from_file(std::istream& file)
{
   int foo, bar;
   file >> foo >> bar;
   return A(foo, bar);
}
```

---

### Post by thumper on 2006-03-01
[QUOTE=krypto_wizard]when do we use the keyword "global" in python ? How can we use it ?[/QUOTE]
Don't.

Or better still, try not to.

---

### Post by krypto_wizard on 2006-03-01
thanks thumper and lordhunter317, you both have been a great help during my pursuit to learn python & OOP.

---

