---
title: "A question about class inheritance and pointers in C++"
date: 2008-06-27
forum: Programming Talk
---

### Post by paukku92 on 2008-06-27
I was just wondering if I should/should not do something like this:

There is a base class, lets say CWidget. It has the basic functions that all GUI widgets have. If I inherit a class for adding some additional stuff, would it be possible to use a CWidget pointer to point to all classes that have been inherited from the CWidget class, so that i could access the basic stuff that every class has.

Would that be a good or bad idea. If so, why?

---

### Post by issih on 2008-06-27
It is a fine idea, and indeed holds a great deal of the whole point of OO programming within it.

If you define a load of different subclasses of "Widget", all of which redefinine some virtual method of the original superclass (e.g. drawWidget) then when the drawWidget method is called through a Widget pointer (actually holding an instance of one of the subclasses) then the method defined in that specific subclass is run, despite the call not knowing anything about the actual specific type of the instance being manipulated.

Because of this you can have for example an array of pointers to animal objects, and just iterate over them to call the peak method.

The Duck overrides speak to print out quack,
The Dog overrides speak to print out bark..

And each object will behave as it should, despite the calling method thinking they are all just Animals.

N.B. This only works through pointers, and using virtual methods, at least in c++

It is worth knowing that if you fail to define a method as virtual, then the version defined in the superclass will be run when the object is accessed through a superclass's pointer. The methods defined on the subclass are effectively hidden and inaccessible ,as are any methods defined solely on the subclass

Hope that helps

---

### Post by paukku92 on 2008-06-27
Thanks for the answer. This makes extending and implementing GUI so much easier when i don't have to define vectors for every type of widget.

---

### Post by escapee on 2008-06-27
Just adding to issih's post, you've stumbled upon Polymorphism!  Congrats on discovering it and it is an great tool to have under your belt.  Google will have plenty of resources if you care to read up on it further.

---

