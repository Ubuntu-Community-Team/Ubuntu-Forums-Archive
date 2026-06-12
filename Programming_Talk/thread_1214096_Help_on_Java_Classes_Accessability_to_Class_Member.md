---
title: "Help on Java Classes Accessability to Class Members"
date: 2009-07-15
forum: Programming Talk
---

### Post by munishvit on 2009-07-15
Hi Guys..):P
Recently I started Java, but got confused in classes (I have a prior knowledge of C). It would be very helpful if one could provide me some short overview (or thru some links) on Inheritance, Nesting, Access specifiers, super, this, abstraction, packages and interfaces. 
Mainly I want to know how the access to a particular member changes on introduction of Nesting, Packages and Interfaces.

---

### Post by PaulM1985 on 2009-07-15
Access modifiers and accessability.

Public has access: within class, package, subclass and world.
Protected has access: within class, package and subclass.
No modifier has access: within class and package.
Private has access: within class only.

Hope this gives a bit of help.

Paul

---

### Post by shadylookin on 2009-07-15
> **munishvit said:**
> Hi Guys..):P
Recently I started Java, but got confused in classes (I have a prior knowledge of C). It would be very helpful if one could provide me some short overview (or thru some links) on Inheritance, Nesting, Access specifiers, super, this, abstraction, packages and interfaces. 
Mainly I want to know how the access to a particular member changes on introduction of Nesting, Packages and Interfaces.

Inheritance. Child(subclasses) classes inherit from parent(super classes)

Nesting. you can write classes inside of classes

access specifiers. public everyone can use, private only class can use, protected everything in the package can use. 

super lets you use something from the super class. 

this. this means "this specific object instance"

abstract . abstract classes are classes that have to be extended and have some abstract function implemented in the subclass

packages are (logical) groups of java classes

interfaces are contracts that says anything that implements this interface will have these methods.

---

### Post by munishvit on 2009-07-17
Thanks guys for helping. :D
I found a useful link too. [http://java.sun.com/docs/books/tutorial/java/](http://java.sun.com/docs/books/tutorial/java/)

---

