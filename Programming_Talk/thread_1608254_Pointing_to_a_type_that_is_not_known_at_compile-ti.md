---
title: "Pointing to a type that is not known at compile-time (c++)."
date: 2010-10-28
forum: Programming Talk
---

### Post by thomas9459 on 2010-10-28
Basically, I want to create a pointer to one of four types of classes in  C++, but I do not know which of the four types to point to until run  time. I would like to have only one pointer to point to any of the  classes. How would I go about doing this, or is it not possible?

---

### Post by worksofcraft on 2010-10-28
This is very easy if you derive all four types from a common base class.
[php]
struct base {};

struct cl1: base {};
struct cl2: base {};
struct cl3: base {};
struct cl4: base {};

// e.g.
base *ptr3 = new cl3;
ptr3 = new cl2;
ptr3 = new cl1;
// etc... and soz about leaking your memory here ;)
[/php]

---

### Post by schauerlich on 2010-10-28
You can either use a void pointer and cast it to a pointer of one of your 4 types before dereferencing it, or if it makes sense within your type hierarchy, make an abstract base class for the 4 types, have each inherit from the base class, and have your pointer be a pointer to the base class. The problem with the second approach is that unless the method signatures will be identical amongst the four classes (and thus you can have a bunch of virtual functions in the base class), you will have to cast it to a specific class to call any methods on the object; you might as well just use a void pointer.

---

### Post by thomas9459 on 2010-10-28
So if all of my classes are derived from a base class, then I can declare a pointer to the base class and point it to a derived class? I never actually took a programming class, I'm just a hobbyist (for now). That works out great as it is easy to do that in my case. Thanks for the help!

---

### Post by GenBattle on 2010-10-28
Just in case you feel like looking it up, this technique is one of many OOP (Object-Oriented Programming) techniques that can come in handy with C++. It is called [Polymorphism]("http://en.wikipedia.org/wiki/Polymorphism_in_object-oriented_programming").

---

