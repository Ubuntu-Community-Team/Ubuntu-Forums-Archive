---
title: "C and Qt"
date: 2009-12-19
forum: Programming Talk
---

### Post by ged25 on 2009-12-19
I've decided to learn some GUI programming. I prefer doing it in C and am trying to decide which toolkit to learn. I know that GTK is used for C programming but I'm wondering if it is possible for me to use Qt. 
So, is it possible to write a Qt application using pure C ?
Thanks..

---

### Post by dwhitney67 on 2009-12-19
Qt is C++ based.  Can a Qt app call upon C functions... yep!

But seriously, if one makes the effort to develop using Qt, they might as well do all of their development in C++.

---

### Post by MadCow108 on 2009-12-19
might want to read this:
[http://www.parashift.com/c++-faq-lite/mixing-c-and-cpp.html](http://www.parashift.com/c++-faq-lite/mixing-c-and-cpp.html)

but I too think its a bad idea. It does not make much sense to me trying to do gui programming with a C++ framework in C.
Also gui programming is naturally object oriented, so a language which actually supports oop syntax is a great advantage.

---

### Post by nvteighen on 2009-12-19
Hm... I think you guys are confusing about using C functions in a C++ program that uses Qt with using Qt in C as you use GTK+ in C... I think the latter is what the OP wants.

The answer is you can't. There's no way to call a C++ library from C... or well, sometimes there is when the C++ library uses the **extern "C" { ... }** idiom and therefore provides a C interface, but that's just able to give you access to functions and structs (i.e. stuff that's present both in C and C++)... but you won't ever be able to use a C++ class in C.

---

### Post by ged25 on 2009-12-20
Thanks for your replies. I've decided to use C++.
I have another question. I read somewhere that the main difference between the LGPL license of Qt and wxwidgets is that Qt does not let you static linking while wxwidgets does.
What is the difference between static linking and dynamic linking ?

---

### Post by Some Penguin on 2009-12-20
Static linking means that the linker takes the relevant bits from the library and embeds them in the binary itself (meaning that it's self-contained, but also that it will not take note of upgraded libraries, that it will be bloated, and that it will not share memory with other applications that instead use the shared library).

Dynamic linking means that the linker instead records a dependency on that library and that the dynamic linker/loader (ld.so) will attempt to resolve the dependency when you run the program.

You need the appropriate library type for the type of linking (typically .a (for 'archive') and .so (for 'shared object')), respectively.

---

### Post by ggeldenhuys on 2009-12-21
> **ged25 said:**
> I've decided to learn some GUI programming. I prefer doing it in C and am trying to decide which toolkit to learn.

If you are not limited to C language, I would highly recommend Lazarus IDE and Free Pascal. [http://www.freepascal.org](http://www.freepascal.org)

It uses the Object Pascal language (no **not** the Pascal language from the '80s). The Lazarus IDE is a RAD (Rapid Application Development) environment and is very easy to use and learn. It uses native GUI toolkits like GTK1, GTK2, Qt, Cocoa or custom written toolkits like fpGUI Toolkit.

This is the quickest and easiest way to develop software and as a bonus your software will be cross-platform enabled with hardly any effort.

---

