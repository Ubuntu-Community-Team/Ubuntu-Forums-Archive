---
title: "Can methods be 'disinherited' in Java?"
date: 2011-04-02
forum: Programming Talk
---

### Post by ownaginatious on 2011-04-02
So I have this super class that can 'produce' and 'consume'. I need to instantiate exactly 1 instance of it.

I also need 'producers' which only produce, and 'consumers' which only consume. Therefore, the way I set it up now has producers and consumers both inherit from the super class capable of both operations.

Now the problem I'm having is, the children inherit all the methods of the parent for consumption and production - when really, each child should only have a subset of the super-class' methods.

Is there a way to do this? Perhaps I'm approaching this the wrong way.

Any advice/help would be appreciated.

Thanks!

---

### Post by slavik on 2011-04-02
you're doing it wrong. if you don't want consumers to produce and producers to consume, then don't have them inherit from the same class.

---

### Post by ownaginatious on 2011-04-02
Alright, but my other option was have the class that both produces and consumes inherit from both producers and consumers... which unfortunately Java does not allow me to do.

Would it be appropriate to create a "producer" and "consumer" interface which simply specify only the methods that pertain to a 'consumer' or 'producer', and then apply it to producer and consumer implementations that just extend the class capable of both?

---

### Post by ve4cib on 2011-04-02
The best way to do this would probably be to use interfaces.  Define a Producer and a Consumer interface and have your classes inherit those as necessary.

Once you've defined an inheritance relationship between two classes it is impossible to "uninherit" public methods defined in the super-class.  That's part of the point of inheritance; any subclasses can be seamlessly treated as the super-class, without needing to worry about methods you expect to be there suddenly vanishing.

---

### Post by Some Penguin on 2011-04-02
I'm a bit puzzled by the first post, because it makes no sense at all to have multiple children extend a class where the parent class must be a singleton.  After all, the multiple children are multiple instances of the parent class and therefore the singleton rule must be violated.

It might make sense for 

* a Consumer interface
* a Producer interface
* some singleton class (singletons should be used with caution...) containing some base functionality... perhaps with its own interface, so you can mock it for test purposes
* implementations of Consumer which accept a reference to the singleton via their constructor
* implementations of Producer which accept a reference to the singleton via their constructor

This will be easier to enforce if you're using an inversion-of-control framework like Spring or Guice, incidentally.

---

### Post by GregBrannon on 2011-04-02
A simple answer to your thread title is that inherited methods cannot be disinherited, but they can be overridden.  Based on the conversation that follows, I'm not sure you were looking for the simple answer, so I apologize if I'm off base.

---

### Post by dazman19 on 2011-04-04
OVERRIDE them.

just make a new function with the same name and signature if its at a lower level it will be overridden.

If you do need to inherit it for whatever reason you can use super().

---

