---
title: "GNOME 3.0 y JAVA"
date: 2007-09-09
forum: Programming Talk
---

### Post by michaelmartin003 on 2007-09-09
KDE 4.0 is near to be release, it is said in December. I rode many about programming languages.
I know that is so good using GNOME or KDE but I want to say something about GNOME and its future.
Programmers know that Qt4 is technologically speaking superior to Gtk+. All people know of the many difficulties of programming in C with Gtk and the wonderful Qt4 libraries of C++ that use KDE.

Well. I would like that the core of GNOME 3.0 should be written in JAVA. This is GPL and at the same time the technology of Java is so good as Qt4. I am not thinking in a flame war of Qt vs Gtk. What I would like is a better superior language core for GNOME. I like GNOME and Java is  the most widely used programming language. So, GNOME 3.0 should have a large community of programmers and a technology like that of KDE and Qt4.
I know of C# and Gtk# but, I think, this is a problem not a solution. Java should be a good option for future of GNOME.

---

### Post by Nekiruhs on 2007-09-09
Java is definitely not the most widely used programming language, just FYI.

---

### Post by CptPicard on 2007-09-09
Bad idea. A windowing toolkit / Desktop environment is resource-intensive enough so that you don't want to be running it on top of a VM like Java's, which in particular does its own memory management outside of the scope of what the OS is doing.

KDE and Gnome are already shaping up to being their own platforms in a lot of ways.. you don't want to build a platform on top of a platform. Your DE needs to be coded fairly low-level so that you can then provide bindings to higher-level languages. That would be difficult to do with Java.

Besides, Java's GUI credentials aren't that great yet.. Swing is still slow. Do you suggest we'd adopt Swing as the toolkit of all applications, or build another one? :) Would all apps then have to be in Java too? :)

---

### Post by kknd on 2007-09-09
No! I completely disagree with you.

The core of the system cannot be written in a language like Java, Python or C#. The developers uses C++ and C to keep memory use at a minimum and give the  best performance.

Look at Solaris and Vista, one has Java, and the other has C# on its core. No big advantage, and they are both memory-hungry.

Java is my main language, but you must know the place of each language.

---

### Post by CptPicard on 2007-09-09
AFAIK Solaris doesn't have "Java at its core". Their DE is branded "Java desktop environment", but it's just a marketing ploy. :)

There is Project Looking Glass though, which is interesting.. I wonder how exactly it integrates with existing non-java applications.

---

### Post by afonic on 2007-09-09
Gnome written in Java? :shock:

Thats like what I would wish to my worst enemy. "I wish your Gnome is written in Java and uses 7GB of RAM. Boo!"

---

### Post by kknd on 2007-09-09
> **CptPicard said:**
> AFAIK Solaris doesn't have "Java at its core". Their DE is branded "Java desktop environment", but it's just a marketing ploy. :).

Yes, you're right =), but there's also a lot of programs that uses Java in it. . The import thing it's that it also consumes a **huge** amount of ram.

I think that softwares that stays running in the background must be written in machine-compiled language. It's awful to look at your memory use and see that one app is using Java other Mono and other python VM's.

---

### Post by tenmillionmilesaway on 2007-09-09
You can already write GTK apps in java, see [http://java-gnome.sourceforge.net/](http://java-gnome.sourceforge.net/).  However as much as I like Java it does use too much memory for it be used to write something like GNOME, and although Java isnt slow, its not as fast as C or C++.

---

### Post by CptPicard on 2007-09-09
> **tenmillionmilesaway said:**
> and although Java isnt slow, its not as fast as C or C++.

It really depends on what kind of code you write. At least a while ago object creation was still quite expensive, and the Java style of spamming lots of little throwaway objects wantonly caused a lot of memory management overhead. I hear this has been fixed somewhat in recent VMs.

One of my number crunching tools that is explicitly written to use a lot of arrays and otherwise minimize memory reference traversal and object creation didn't really benefit at all from porting to C++; the JIT compiler does a good job.

---

### Post by pmasiar on 2007-09-09
> **michaelmartin003 said:**
> Well. I would like that the core of GNOME 3.0 should be written in JAVA. ...I like GNOME and Java is  the most widely used programming language. 

It is bad idea and will not happen for couple reasons:

1) Gnome is in C, take it or leave it. Thousands of hours were spend to optimize it and fix the bugs. No sane project manager would throw working code and rebuild from scratch in different language to satisfy some language preferences. Too late. This one reason is enough.

2) Gnome is in C, which is low-level language with exact memory management. Java is much higher level, harder to optimize. Also, Java is build on top of JVM, which is multiplatform. C has different way to be multiplatform, and I have every reason to believe it is superior. At least in eyes of it's developers, who has **full control** over how it is done. Java is unproven in this POV.

3) Java is definitely **not** the most used language, and although it will remain popular for 30 more years, the fact Sun converted it it GPL proves that Java alone was not able to become **the** platform on its own, and needed GPL compatibility to remain viable. Future belongs to C for low-level libraries written for effectiveness, and dynamically typed languages like Python gluing it together. Special bonus to multi-threaded languages like Erlang.

---

### Post by malfist on 2007-09-09
As much as I love java, I have to disagree, building a DE on Java whos own UI isn't finished is a bad idea. Java claims that Swing may not be compatiable with future versions of Swing, which isn't good.

Java is really nice and I love it, but I wouldn't recommend it for this type of thing. I'd say C/C++.

edit: maybe python? I don't know much about python so I may be wrong in that.

---

### Post by pmasiar on 2007-09-09
> **malfist said:**
> maybe python? I don't know much about python so I may be wrong in that.

As much as I love Python :-) , I would not recommend switching to Python for reason (1). But I want to add,  [http://en.wikipedia.org/wiki/Olpc](http://en.wikipedia.org/wiki/Olpc) uses GUI Sugar, written in Python.

---

### Post by afonic on 2007-09-10
I guess this topic is pretty useless. :P

Gnome is written in C, what is wrong with C? :)

If anyone wants to write some program for Gnome it doesn't mean he should use C, he can use whatever he wants.

---

### Post by samjh on 2007-09-10
Although I like Java, an operating system and its core GUI should NOT be written in Java, or in any interpreted or VM-reliant language.

C and C++ provide high speed of execution, low processor and memory consumption, and detailed access to low-level system resources.  These are very important characteristics of programming languages used for operating systems and core GUIs.

The less resources consumed for core functionality, the more resources there are for user applications.  And like it or not, user applications are what makes computers accessible!

If Gnome was re-written in Java (or C#, Python, Ruby, etc.), we'd end up with as much capability-per-clock-cycle as a decade ago.  I'd rather not rewind the clock that far.  It might even be worse for QT, although QT-Jambi (QT for Java) is quite a neat idea.

---

### Post by aks44 on 2007-09-10
> **samjh said:**
> an operating system and its core GUI should NOT be written in Java, or in any interpreted or VM-reliant language.

Go say that to Microsoft and their [Singularity]("http://en.wikipedia.org/wiki/Singularity_(operating_system)") research OS fully written in C# (even the kernel).
They went as far in "innovation" as to completely ditch the concept of shared libraries, each and every program has to include all it's dependencies as static libraries in a single monolithic binary.

All hail VMs and managed code, they are the future! :lolflag:

---

### Post by pmasiar on 2007-09-10
> **aks44 said:**
> Go say that to Microsoft and their [Singularity]("http://en.wikipedia.org/wiki/Singularity_(operating_system)") research OS fully written in C# (even the kernel).


But C# IIUC is not supposed to be as multiplatform as java wants to be. And MSFT was never afraid to tax hardware to max and then suggest users to upgrade :-)

---

### Post by samjh on 2007-09-10
> **aks44 said:**
> All hail VMs and managed code, they are the future! :lolflag:

Well... yes.  But not for operating systems.

Even Microsoft writes Windows with C and C++, although that's probably a counter-productive example to the point I was trying to make! :p

---

