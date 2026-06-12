---
title: "[SOLVED] C++ noob GUI"
date: 2008-06-20
forum: Programming Talk
---

### Post by Rhaddad on 2008-06-20
Hello, can anyone tell me the equivilant of Jframe and jswing in C++?
like the classes used to make GUIs

---

### Post by xlinuks on 2008-06-20
There are several GUI libraries: GTK, QT and others. Gnome is based on GTK and is written in C.
KDE is based on QT and is written in C++ (with some dirty implementations).
To use C++ with GTK there is "Gtkmm" that binds C++ to GTK.
For more info have a look here:
[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-gtkmm.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-gtkmm.html)

PS: I'm also coming from Java to C++ and I think you'll also be pretty much frustrated missing different things you had for granted in Java and finding that doing some things requires "weird" techniques. I'm doing an app and still wondering why the library/libraries is/are so "inaccurate".

---

### Post by Rhaddad on 2008-06-20
Yea it's weird, like i have to get KDE libraries and stuff, while in JAVA you have one library for all platforms.

---

### Post by Jessehk on 2008-06-20
> **xlinuks said:**
> 
KDE is based on QT and is written in C++ (**with some dirty implementations**).


Huh? Please eloborate.

---

### Post by xlinuks on 2008-06-20
> **Jessehk said:**
> Huh? Please eloborate.

> 
gtkmm compared to QT

Trolltech's QT is the closest competition to gtkmm, so it deserves discussion.

gtkmm developers tend to prefer gtkmm to QT because gtkmm does things in a more C++ way. QT originates from a time when C++ and the standard library were not standardised or well supported by compilers. It therefore duplicates a lot of stuff that is now in the standard library, such as containers and type information. Most significantly, Trolltech modified the C++ language to provide signals, so that QT classes can not be used easily with non-QT classes. gtkmm was able to use standard C++ to provide signals without changing the C++ language. See the FAQ for more detailed differences.


The source:
[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-gtkmm.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/sec-gtkmm.html)

---

### Post by StOoZ on 2008-06-20
> **Rhaddad said:**
> Yea it's weird, like i have to get KDE libraries and stuff, while in JAVA you have one library for all platforms.

I never used java, but what do you mean by that?
that u write the GUI in linux with the same lib u used in Linux?!?!? 
if so , thats COOL!!

---

### Post by Rhaddad on 2008-06-20
Stooz thats exactly right, you use the same library for writting code in java for everything. 

You only compile once into byte code. then your java Virtual machine interprates it. So it can run on many platforms and only need to be compiled once

---

### Post by StOoZ on 2008-06-20
Sounds cool , I wish C++ was like that... (well , Qt is almost like that... )

---

### Post by LaRoza on 2008-06-20
> **StOoZ said:**
> Sounds cool , I wish C++ was like that... (well , Qt is almost like that... )

C++ has a different purpose than Java. Java is an entire platform, C++ isn't.

---

### Post by StOoZ on 2008-06-20
> **LaRoza said:**
> C++ has a different purpose than Java. Java is an entire platform, C++ isn't.

I dont get it , can you please explain it?

thanks,

---

### Post by LaRoza on 2008-06-20
> **StOoZ said:**
> I dont get it , can you please explain it?

thanks,

Ok, Java specifications describe a platform for running software. Basically, Java is a virtual hardware. So, to use Java, you need the JVM installed. The JVM is a virtual machine (there also may be hardware Java). Java the language is compiled to run on this machine, so anywhere the JVM exists, Java can run. This allows the exact same program to run on any operating system that has the JVM.

Also, it allows other languages to be used on this platform. Lisp, Python, Ruby and others have all been ported to the JVM, so one can actually write Java applets in Python (Jython, the code is compiled to the byte code)

---

### Post by Npl on 2008-06-20
> **StOoZ said:**
> Sounds cool , I wish C++ was like that... (well , Qt is almost like that... )Only if you are content with the choices of the Java-Library. They have 1 Gui-Library - Swing (ok, two with AWT which noone uses), if you want to use something else you need an additional library, SWT beeing an example (eclipse and azureus both dont use Swing, but SWT).
With C++ there is no standard GUI, which has the advantage that C++ programs have way less requirements to run.

---

### Post by xlinuks on 2008-06-20
> **Npl said:**
> Only if you are content with the choices of the Java-Library. They have 1 Gui-Library - Swing (ok, two with AWT which noone uses), if you want to use something else you need an additional library, SWT beeing an example (eclipse and azureus both dont use Swing, but SWT).
With C++ there is no standard GUI, which has the advantage that C++ programs have way less requirements to run.

What kind of "requirements to run" do you mean?
First off C++ is a language while "Java" is a "technology", which means the language, the libraries for GUI/IO/encryption and lots of other stuff not necessarily bound to libraries only. If you don't wish to use those libraries - you are free to do so, you are free to use whatever libraries you wish, there are third party libraries that bind Java to Gtk and and for a lot of other stuff.

---

### Post by Npl on 2008-06-20
> **xlinuks said:**
> What kind of "requirements to run" do you mean?
First off C++ is a language while "Java" is a "technology", which means the language, the libraries for GUI/IO/encryption and lots of other stuff not necessarily bound to libraries only. If you don't wish to use those libraries - you are free to do so, you are free to use whatever libraries you wish, there are third party libraries that bind Java to Gtk and and for a lot of other stuff.Java is no "Technology", its a Language, its a library and a platform. C++ is only a Language and a library. If you consider it a Technology, then all other languages pass as Technology too.

I dont know why you are arguing with anyway, did you read the post I was replying too?.
My point was that Java has a GUI-Component in its standard library, but that does mean that complying environments are (severly) bigger than C++ ones. And if you choose to use a additional library like SWT its no different to using a library for C++

---

### Post by xlinuks on 2008-06-20
Haha. You are priceless.
Java _is_ technology, do you know Sun Microsystems? You should really read their tutorial or at least read the title of their page at [http://java.sun.com](http://java.sun.com)
They are wrong, right? Why don't you tell them that you better know what Java is and prove that to them. You are very smart.

---

### Post by Rhaddad on 2008-06-20
Java is slow because it doesn't compile to Machine Code (as in binary). Like in C++ it compiles it straight to binary and only runs on the platform were it was compiled from (Most of the time), therefor during execusion only binary codes are sent to the CPU to be executed, as the CPU may only read Binary.

However with java it compiles to byte code. and to read that byte code you need a Java Virtual machine, and this is what makes java so slow because during execution it translates to binary, while in C++ it is allready in binary. And that Why java may run on many systems

XLinuks this is taken straight from the Java site
These tools and web sites teach young people how to program using the _Java programming language_, as well as languages developed for ease of use.

---

### Post by dwhitney67 on 2008-06-20
Java doesn't have to be slow.  Many Java developers who consider themselves "experts" with Java haven't a clue that Sun Microsystems originally touted the language as one that could be used within embedded systems.  Most Java developers strayed from that original concept and nowadays use it merely for GUI development.  Such as shame!

Want to compile a Java application to run on a dedicated architecture, similar to a C++ application?  Then use the [JIT]("http://en.wikipedia.org/wiki/Just-in-time_compilation") (Just In Time) compiler.

Btw, this thread has migrated so far off topic that I think you should close it now.

---

### Post by Rhaddad on 2008-06-21
Yea i will.

I'll just stick with Java for now. Screw C++.

---

### Post by dwhitney67 on 2008-06-21
Great!  Thanks for wasting everybody's time with this worthless thread.  C++ can be used, and is used, as the language of choice for many applications in this world and outside (i.e. satellites, spacecraft, etc).

It would seem that in your case you have found C++ to be too challenging and have decided thrown in the towel.  Up to you.

Such as shame that you did not consider that for many applications, C++ is used for the back-end (or middle-ware) portion of the application, and the GUI is written Java, Gtk+, Qt, or whatever.

With the MVC (model-view-controller) approach to a design, it becomes an issue of preference as to which language will be used for the GUI.

Anyhow, good luck with endeavours.

---

### Post by xlinuks on 2008-06-21
dwhitney67 you should respect his/people's decision(s) and according to the "traditions" of the Ubuntu community I would suggest being more polite.
I think it might not be the right time for him to switch to C++. I was considering moving to C++ (from a Java background) several years ago but only a few month ago actually started learning it. And now I guess I did the right thing in the right time, and I realize that the same issue happens to other people, Rhaddad being an example.

---

### Post by dwhitney67 on 2008-06-21
Oh, I do respect his decision... actually, I am ambivalent.  But to start a thread seeking an answer, and then to discount all worthy advice to merely state that he is returning to the comfort of a language that he has presumably already mastered, is a slap in the face to everyone that offered advice.

In the future, perhaps the first posting to a thread similar to this one ought to be responded to with the term "troll!".

---

