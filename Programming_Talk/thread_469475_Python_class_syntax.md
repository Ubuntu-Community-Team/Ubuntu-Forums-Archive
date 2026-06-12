---
title: "Python class syntax"
date: 2007-06-09
forum: Programming Talk
---

### Post by kevinlyfellow on 2007-06-09
I've been moving right along learning python, and I've just been introduced to classes.  But I'm having a bit of difficulty understanding the syntax.

Here is the example I'm given
```

class Square:
  def __init__(self, side):
    self.side = side
  def calculateArea(self):
    return self.side**2

```

What exactly is "self"?  why do I need to say things like self.side?

---

### Post by reacocard on 2007-06-09
> **kevinlyfellow said:**
> I've been moving right along learning python, and I've just been introduced to classes.  But I'm having a bit of difficulty understanding the syntax.

Here is the example I'm given
```

class Square:
  def __init__(self, side):
    self.side = side
  def calculateArea(self):
    return self.side**2

```

What exactly is "self"?  why do I need to say things like self.side?

self is a reference to the class itself. When you want to store or access data in the class from within the class, you have to use self. Without self, it's just a local variable, which disappears when no longer needed (usually at the end of the method it's in).

---

### Post by kevinlyfellow on 2007-06-09
So, self.side is created so that we can put the variable side in each new definition in the class?  This must be the reason the calculateArea has the parameter "self".  It brings in all variables that belong to self... Am I confused?

---

### Post by pmasiar on 2007-06-09
More exactly, self is reference not to the classX, but to instance  of the object (of type classX). So you can access instance's methods and attributes, and distinguish them from normal local variables.

Don't worry too much about defining your own classes now: you know how to use existing classes, and you can get feeling about programming without OOP. Untill your program has 1000 lines, OOP will not be that important. Data structures (list, dictionaries) are more important that defining classes. You can return to objects later. Just know how to use them.

---

### Post by n0dl on 2007-06-10
If you have any experience in C or C++ everything in python in pass by refrence. self to be more exact is a refrence to the current instance that is using it, a pointer, if you will. Remember that a class is a psuedo object and not the actual class. For example
```
class Square:
  def __init__(self, side):
    self.side = side
  def calculateArea(self):
    return self.side**2
def main():
    parallelogram = Square(2)

```
parallelogram now replaces self because parallelogram _IS_ the object. So self.side could be thought of as parallelogram.side = 2 (the 2 taken from the argument passed when instantiated. To be more clear I shall present another example
```

    #Again in main
    another_parallelogram = Square(5)
    parallelogram.calculateArea()
    another_parallelogram.calculateArea()

```
Instantiating another object, another_parallelogram in this case, _IT'S_ value for side is 5, Basically the name of the object replaces the word self during instantiation during the assignments of it's attributes. The value for parallelogram.side is completly different from another_parallelogram.side 's value. In terms of self as an argument it, in a metaphysical sense, helps the class know which instance (or object interchangebly) is calling the method. parallelogram.calculateArea() 's result is going to be very different from another_parallelogram 's result because of their values for their sides. So think of it this way. When the call statement, another_parallelogram.calculateArea() is called another_parallelogram is passed an an argument.Therefore all attributes of **another_parallelogram** is called and not any other instance's attributes (such as parallelogram's attributes).

---

### Post by kevinlyfellow on 2007-06-10
> **n0dl said:**
> If you have any experience in C or C++ everything in python in pass by refrence. self to be more exact is a refrence to the current instance that is using it, a pointer, if you will. Remember that a class is a sudo object and not the actual class. For example
```
class Square:
  def __init__(self, side):
    self.side = side
  def calculateArea(self):
    return self.side**2
def main():
    parallelogram = Square(2)

```
parallelogram now replaces self because parallelogram _IS_ the object. So self.side could be thought of as parallelogram.side = 2 (the 2 taken from the argument passed when instantiated. To be more clear I shall present another example
```

    #Again in main
    another_parallelogram = Square(5)
    parallelogram.calculateArea()
    another_parallelogram.calculateArea()

```
Instantiating another object, another_parallelogram in this case, _IT'S_ value for side is 5, Basically the name of the object replaces the word self during instantiation during the assignments of it's attributes. The value for parallelogram.side is completly different from another_parallelogram.side 's value. In terms of self as an argument it, in a metaphysical sense, helps the class know which instance (or object interchangebly) is calling the method. parallelogram.calculateArea() 's result is going to be very different from another_parallelogram 's result because of their values for their sides. So think of it this way. When the call statement, another_parallelogram.calculateArea() is called another_parallelogram is passed an an argument.Therefore all attributes of **another_parallelogram** is called and not any other instance's attributes (such as parallelogram's attributes).

Thanks... I think that is what I needed.  Just to make sure I'm straight on this.  
```

  def __init__(self, side):

```
We bring the object (parallelogram) as a parameter into the initialization function along with the parameter "side".  

```

    self.side=side

```
Here we gave the object parallelogram a property (side).  This property has a scope that is limited to the class?  Could we have just as easily said
```

    self.elephant = side

```
without any problems?

```

  def calculateArea(self):

```
We are using the object (self or the parallelogram) as a parameter in this "function" (is that the right term?).  It keeps all properties that it has from __init__

---

### Post by n0dl on 2007-06-10
Yes you are correct on the self.elephant comment.However you are wrong when you said
> This property has a scope that is limited to the class? 
You are close though. The scope is not limited to the class but the _object_ itself. By limiting the scope to a single object we are able to focus on the parallelogram's value of elephant, or the another_parallelogram's value of elephant exclusively.
When talking about a function that is a member of a class you call it a method. A set of statements independent of any class is called a function .Often times the difference is that in a function self is not given as an argument when defining it because it does not have access to the attributes of an object (or instance interchangebly) as defined in it's instantiation _method_. The method, calculateArea(), as you have mentioned at the bottom, _will_ keep all the attributes from the __init__ method as you have said. But do not forget that the method's definition will also be changed as well.
```
  def calculateArea(self):
    return self.side**2
```
the self.side**2 will have to be changed to
```
return self.elephant**2
```
since the attribute elephant now contains the length of a single side as you have assigned it in the __init__ method.

---

### Post by pmasiar on 2007-06-10
> **n0dl said:**
> If you have any experience in C or C++ everything in python in pass by refrence. .

**Not true**. Non-mutable objects (i.e: scalar, string, etc) are passed by value.

> self to be more exact is a refrence to the current instance that is using it, a pointer, if you will. 

True. 'self' is used by convention, but you can use any name which makes sense to you, like 'this' or anything.

Python does not have pointers (pointing to untyped area in memory): all references keep the type of the value (valid methods which can be used with it).

> Remember that a class is a psuedo object and not the actual class. 

**This sentence does not make any sense at all.**

Think about **class as cookie cutter, and instance as cookie make by that cutter**. You can make many different instances (cookies) of same class (using same cookie cutter). All instances will have some common attributes (like shape) and some specific values (ie different dough or frosting)

Class is *not* an object. **Class is a way how to create new objects** and give then some common characteristics (and allow for some controlled customization).

Let's translate sentence above to cookies terminology:

"Remember that a cookie-cutter is a psuedo cookie and not the actual cookie-cutter."

See, it does not make any sense.

Remember that a class is not an instance of an object. 

Class is a way to create instances - calling the __init__() method.

But as I said, until you want to create your own objects, you don't care much about it. People were able to write programs for 30 years without objects, and Python allows you to postpone OOP until you are ready and need it - unlike other languages, like Java, which are object-obsessed and you *have* to use objects from the day one, even if your task does not need them.

---

### Post by kevinlyfellow on 2007-06-10
Thanks everyone!  You were all very helpful.

---

### Post by n0dl on 2007-06-10
> > Remember that a class is a psuedo object and not the actual class.

This sentence does not make any sense at all.

*face palms* Pmsiar Thanks for catching that. It was late when i wrote my resonse.
What i meant to say was a class is a psuedo object and not the actual object. A class is a factory to produce objects.(as you have iterated above using cookies as an example)

---

