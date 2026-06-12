---
title: "What is module in terms of Object Oriented Programming"
date: 2010-09-27
forum: Programming Talk
---

### Post by gozlemci on 2010-09-27
Hi there;
In Code complete, author Mr Steve McConnell mentioned "module" in page 89.

> 
Semantic coupling 
The most insidious kind of coupling occurs when one module makes use not
of some syntactic element of another module but of some semantic knowledge of another
module's inner workings. Here are some examples:

* Module1 passes a control flag to Module2 that tells Module2 what to do. This approach
requires Module1 to make assumptions about the internal workings of Module2, namely
what Module2 is going to do with the control flag. If Module2 defines a specific data type
for the control flag (enumerated type or object), this usage is probably OK.

* Module2 uses global data after the global data has been modified by Module1. This
approach requires Module2 to assume that Module1 has modified the data in the ways
Module2 needs it to be modified, and that Module1 has been called at the right time

* Module1's interface states that its Module1.Initialize() routine should be called before its
Module1.Routine() is called. Module2 knows that Module1.Routine() calls
Module1.Initialize() anyway, so it just instantiates Module1 and calls Module1.Routine()
without calling Module1.Initialize() first.

* Module1 passes Object to Module2. Because Module1 knows that Module2 uses only
three of Object's seven methods, it initializes Object only partially—with the specific data
those three methods need.

* Module1 passes BaseObject to Module2. Because Module2 knows that Module1 is really
passing it DerivedObject, it casts BaseObject to DerivedObject and calls methods that are
specific to DerivedObject.

what does he mean by the word "module"? Can anybody describe it briefly? Thanks in advance.

---

### Post by r-senior on 2010-09-27
I think in that context, he's talking about a class and the concept of encapsulation, i.e. a class should be a black-box and the class that utilises it should not have any responsibility for how the utilised class works.

---

### Post by Bachstelze on 2010-09-27
The same applies to any module really, not only in OOP.  It's probably a bad idea to make assumptions about how someone else's code works.

---

### Post by gozlemci on 2010-09-27
It seems I've missed the point at page 87. Here Mr McConnell said:

> 
Coupling describes how tightly a class or routine is related to other classes or routines. The goal
is to create classes and routines with small, direct, visible, and flexible relations to other classes
and routines, which is known as "loose coupling." The concept of coupling applies equally to
classes and routines, so for the rest of this discussion I'll use the word "module" to refer to both
classes and routines. 
I 've assumed that it is a jargon in programming languages. Thank you for your interest* r-senior* and *Bachstelze*.

---

### Post by worksofcraft on 2010-09-27
That is a slightly confusing use of terminology because to me a "module" has always meant something that the linker/loader combines to produce a working program.

However the things he says apply equally to these link/loader object modules and in much C legacy code a huge number of problems come from this kind of coupling where things in libraries need to be cast into other things based on knowledge of internal working of said library.

The way to avoid it is by using polymorphism: The objects themselves are responsible for selecting appropriate methods and the caller doesn't have to distinguish it from it's base class.

---

