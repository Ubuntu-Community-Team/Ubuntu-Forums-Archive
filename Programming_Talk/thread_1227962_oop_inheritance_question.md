---
title: "oop inheritance question"
date: 2009-07-31
forum: Programming Talk
---

### Post by abhilashm86 on 2009-07-31
when i create a base/parent class, use inheritance to make a derived class.
So if i add or remove members of the base class, it will also affect derived class.......
basically code re-use and constant changes of base class need to clashes.........
so what i exactly declare my derived class, so changes in base class wont affect my derived class?

---

### Post by jespdj on 2009-07-31
Inheritance in object oriented programming indicates an [is-a](http://en.wikipedia.org/wiki/Is-a) relationship: an instance of the subclass **is a** (specialized version of) an instance of the superclass.

So, inheritance tightly couples superclasses and subclasses, and it's to be expected that when you change something in the superclass, this will most likely have effects on subclasses.

Using inheritance just because you want to reuse code is not a good idea. [Wikipedia](http://en.wikipedia.org/wiki/Inheritance_(computer_science)) explains it clearly:

> Code re-use

One of the earliest motivations for using inheritance was to allow a new class to re-use code which already existed in another class. This practice is usually called implementation inheritance.

In most quarters, class inheritance for the sole purpose of code re-use has fallen out of favor. The primary concern is that implementation inheritance does not provide any assurance of polymorphic substitutability—an instance of the re-using class cannot necessarily be substituted for an instance of the inherited class. An alternative technique, delegation, requires more programming effort but avoids the substitutability issue. In C++ private inheritance can be used as form of implementation inheritance without substitutability. Whereas public inheritance represents an "is-a" relationship and delegation represents a "has-a" relationship, private (and protected) inheritance can be thought of as an "is implemented in terms of" relationship[1].

---

### Post by cobolt01 on 2009-07-31
There should never be a reason to re-write child classes due to a change in a parent class.
If you're having trouble understanding inheritance, think of it like this.

Animal
-Bird
--Duck

A duck is a bird which is an animal. Therefore, all attributes common to all animals are also included in all birds and therefore ducks through inheritance.

---

### Post by abhilashm86 on 2009-07-31
yes i think it'll be more tough when i change base class just to do some alterations, but when more sub classes are there, i can just again inherit the base class and modify and use it, that makes better sense.......
while i was looking is-a and is-like-a relationships, i just thought about it, yes i do see other major functions......
thanks

---

### Post by jespdj on 2009-08-06
> **cobolt01 said:**
> There should never be a reason to re-write child classes due to a change in a parent class.
That's not true.

Subclasses inherit the interface and implementation of superclasses. If you change a superclass, then that has a direct impact on the subclasses of that superclass, and there's a larger chance that you'll have to change the subclass too.

That's why I said that inheritance tightly couples superclasses and subclasses.

---

