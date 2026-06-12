---
title: "C++ frameworks"
date: 2008-11-30
forum: Programming Talk
---

### Post by Sydius on 2008-11-30
I borrowed a copy of "Design Patterns: Elements of Reusable Object-Oriented Software" from a library, and I've been soaking it up like a sponge.  Really interesting stuff to me, even if it was written in '94.

It made me wonder if there are any well-known C++ frameworks.  In the PHP world, there are MVC-like frameworks (I say "like" because I have come to realize the way they are used is rarely in the spirit of MVC) such as CodeIgniter, Kohana, etc.  But I have never run across what I would consider the equivalent for C++.

There are toolkits that provide services, and some C frameworks like SDL (I don't know if you would call that a framework?).  I have seen C++ wrappers for C frameworks, but those don't usually do much beyond RAII (the wrapper is very thin).  I've used C++ "engines" like Ogre3D which might be called a framework.

But what I am more interested in, after reading this book, is if there are any well-known/tested frameworks for C++ that work to define a system architecture more than a thin wrapper on top of a C framework.  I am especially interested in knowing about any that document the design patterns they use and how (since that is what I am learning about), particularly if they provide accompanying UML diagrams (another thing I am learning).

What are people using? I know they can (and often are) domain-specific, but I am still interested.

---

### Post by meatpan on 2008-11-30
Good question.

For starters, consider the Boost framework.  All code is peer-reviewed, well debugged, and actively supported.  [http://www.boost.org](http://www.boost.org)

Some excellent implementations of design patterns can be found in the 'loki' framework:  [http://loki-lib.sourceforge.net/](http://loki-lib.sourceforge.net/)

If you find anything else, let me know!

---

### Post by Sydius on 2008-12-01
I was familiar with Boost, but not with Loki, so I appreciate the information.  I don't believe either are frameworks in the sense that I meant, though.

The distinguishing feature of frameworks as opposed to libraries or toolkits, according to Wikipedia, is that they provide the inverted relationship between caller and callee.  In the case of Boost and Loki, the main application calls on those classes and methods to augment the main functionality of the program, whereas with a framework, the application is defined in code that is called by the framework.  So the framework takes some amount of burden off of designing the overall system architecture, while Boost and Loki simply provide tools to implement an architecture more easily.

At least that's my understanding.  In any case, I appreciate being shown Loki. I think it might be close enough to what I was interested in finding. :)

---

### Post by dribeas on 2008-12-01
> **Sydius said:**
> But what I am more interested in, after reading this book, is if there are any well-known/tested frameworks for C++ that work to define a system architecture more than a thin wrapper on top of a C framework.

If you talk communications and networking you can check [ACE]("http://www.cs.wustl.edu/~schmidt/ACE.html"). [Boost]("http://www.boost.org"), as you said is more centered in providing libraries than a framework, in the same line as [PoCo]("http://pocoproject.org/"). 

[Qt]("http://trolltech.com/products") is a framework (more than just graphic stuff, and it is not quite pure C++), and as far as I know [wxWidgets]("http://www.wxwidgets.org/") is another framework. They both provide a windows toolkit, but also other types of components.

---

### Post by samjh on 2008-12-01
Qt: [http://en.wikipedia.org/wiki/Qt_(toolkit](http://en.wikipedia.org/wiki/Qt_(toolkit))

On Ubuntu it can be installed with: sudo apt-get install qt4-dev-tools
Licensed under GPL v2 and v3 for the Open Source edition.

It has very good tutorials too: [http://doc.trolltech.com/4.4/tutorials.html](http://doc.trolltech.com/4.4/tutorials.html) :)

Oh, and just to clarify what Dribeas said about it not being pure C++:
It only deviates from ISO-standard C++ when you define your own signals and slots, and all non-standard C++ code is handled by the meta-object compiler (you just need to run the qmake command as part of the build process) so you don't really need to think about the non-standard C++ bits.

---

