---
title: "What's the point of classes?"
date: 2007-09-10
forum: Programming Talk
---

### Post by Anonii on 2007-09-10
Hello,

I've been reading Dive Into Python, and I just reached the Object-Oriented Programming section which talks about classes. Unfortunately, my only programming experience is with a local translation of Pascal (Back in highschool) and I really can't connect Python's classes with anything Pascal-ish.
Basically, I can't understand what's the point of classes. I bet they are not there to point out the sections of code. I have heard something about class instances but I still don't get it. Is it that the functions inside a class can only be called from code inside that class? And what's the use of it?

D:

---

### Post by CptPicard on 2007-09-10
Python is a dynamically typed language so Python's classes are not necessarily the best representation of the very idea of classes... let's talk about statically typed language classes, like in Java or C++. :)

Classes come from type theory. Just as you have integers, strings, and other data types, classes are a way to define new types that have in addition to an amount of data, also *operations* (class "methods", functions specific to that class) that operate on that data.

First of all, an important distinction: a *class* is a blueprint of an *object*. You *instantiate* an object based on its class definition, at which point memory is reserved for data members, which can have different values for each separate object. From this point on forward, each object behaves according to its class definition.

Classes provide you with new important concepts... encapsulation, inheritance and polymorphism.

Encapsulation allows you to hide implementation details and data members that should be kept private from outside interference. The corollary is that the public interface of the class -- those members and methods that are visible to everyone -- forms the *contract* of the class with the outside world. If the class promises to doSomething(), as the user of the class, you are not interested in the specifics of how exactly this is accomplished; you just call the public method of that name. Then the object does its thing using its internal definitions and data values specific to that object.

Inheritance allows you to form inheritance hierarchies of classes. This forms an "is-a" relationship between two levels of classes. The idea is that if you have a parent class with child classes, you can always substitute an object of a child class type with another child class type, as long as you just use the object as if it represents "only" the parent class. Each child can implements its internals differently -- this is polymorphism -- but the point is that you don't really care :)

This might sound difficult, but it really is not... think of the type hierarchy of number theory. Both integers and rational numbers are real numbers. They both behave according to the "real number class" as far as those operations go you can perform on them. So you could define addition and subtraction and multiplication on them, but actually implement them differently for both ints and rationals. Then when you want to do some generic math, you can just *use the generally agreed upon operations that all reals have* without really caring whether under the hood you're getting integer addition, rational addition or maybe an int-rational addition!

Object oriented programming is really a type system and modularisation issue, that at least is supposed to provide for example code reusability benefits. YMMV, and there are lots of philosophical discussions on OOPs merits on the net...

---

### Post by pmasiar on 2007-09-10
class is your custom data type, bundled with functions (called methods) to perform activities.

You are lucky you use Python, so don't worry about classes and write plain old procedural programs. gradually, you learn how classes are used by using standard libraries, and then you can think about defining your own classes. 

But don't worry about it now.

If you are beginner, "dive into Python " might be too steep learning curve for you. Why won't you use something more oriented to beginners? See wiki in my sig.

---

### Post by Wybiral on 2007-09-10
> **pmasiar said:**
> You are lucky you use Python, so don't worry about classes and write plain old procedural programs.

There's nothing to worry about classes really... They are just a convenient way to: group data (function and variable data) in a meaningful way, make it easy to pass data around (you don't have to pass EVERY variable around, but you can wrap them in a class and pass that object), and they help with namespace issues since different objects can use the same labels for members and methods without collision.

This isn't even mentioning the really neat aspects they bring, like genericness and code reuse.

---

