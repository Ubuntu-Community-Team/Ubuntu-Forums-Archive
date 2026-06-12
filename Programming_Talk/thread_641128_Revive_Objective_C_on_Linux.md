---
title: "Revive Objective C on Linux"
date: 2007-12-15
forum: Programming Talk
---

### Post by netkid91 on 2007-12-15
Why did such a great language die?  Is it because no UI lib has bindings for it beside GNUstep?

I have been playing with it, and have decided I would at least fix the issue of UI libraries.  So I am making [obgtk]("http://obgtk.googlecode.com"), a effort to provide fully OO access to GTK with native Objective C classes.

Currently all that is done is a few parts of GTKWindow, and GTKButton, GTKWidget, and GTKContainer classes to rewrite the GTK "Hello world" app in Objective C.  Although since GTK is based on GObject mapping the rest of the library will be very easy.

BTW, here is the source for the ObjC GTK "Hello world app"
[http://obgtk.googlecode.com/svn/trunk/WidgetDemo/WidgetDemo.m](http://obgtk.googlecode.com/svn/trunk/WidgetDemo/WidgetDemo.m)

---

### Post by H264 on 2007-12-15
Hi.. Yes, Objective-C is a great language and right now good libraries are shortcoming the language more or less, however you are doing duplicate work.

If you would hang out in ##objc (freenode.net) you would know that there is already a guy that has been doing GTK2 wrappers for ObjC. There is also a Jewl in the rough (so to speak) regarding an offshoot of GNUstep called SideStep. SideStep's goal is to clean out the gruff in GNUstep and have a separate windowing lib based totally in SideStep.

Neither projects have a website, so you might as well hang out in #sidestep and ##objc :popcorn:

I don't know enough C yet to be of any use.. I'm working on that part. ;)

Cheers

---

### Post by Majorix on 2007-12-15
Instead of trying to revive a pretty much dead programming language (which doesn't have any good compilers or libraries), you could just as well go the C++ way, which was once called "C with Classes" and is pretty much an "objective" C.

---

### Post by xtacocorex on 2007-12-16
Objective-C is not dead, it is used widely for OS X application development, mainly due to it's roots in NeXTStep which Job's helped create.

The GNU C/C++ compiler will compile Objective-C code, I did so on my Mac this morning, and since it's a cross platform compiler, it should do the same on Linux.

---

### Post by netkid91 on 2007-12-16
> **Majorix said:**
> Instead of trying to revive a pretty much dead programming language (which doesn't have any good compilers or libraries), you could just as well go the C++ way, which was once called "C with Classes" and is pretty much an "objective" C.
Objective C is not dead, it is very much alive.  Also, Objective C is "C with classes", C++ is a different beast altogether, and is far from C with OO tacked on.

Also, C++ is no where CLOSE to Objective C in terms of...anything.  C++ is statically typed for one, while objective C isn't.  Also, Objective C doesn't check to see if objects can receive a message until runtime, which is a curse and a blessing all at once.

As stated above, gcc can compile objc, especially since apple uses the language.  It's alive and well, and I think it needs to be used more outside of the apple world.

---

### Post by engla on 2007-12-17
obgtk would need a more automatic bindings generation; otherwise keeping up with changes in gtk is not going to work. For example, perhaps it would be possible to wrap just the base object and by introspection provide the basic function of other methods for most classes. One problem with obj-c is of course that it would be nice to transfer function calls into nice obj-c selectors.

Objective-C is cool, it was the first language I learnt for object-oriented programming. The object model is very interesting and the language is totally dynamic.

<storytelling voice>
Also, there is a curiosity called *Objective-C++*: it's not a language, it is just a reference to a way to use gcc where you can compile C++ and Objective-C code together. I once submitted some patches to the Camino project (Mac OS X browser); that application is based on Mozilla Gecko (which uses C++) and the Cocoa UI toolkit, using Objective-C; hence it is compiled as "Objective-C++". The two languages and their object models don't interoperate at all, but their objects can store pointers to objects of the other type, of course.

---

### Post by macogw on 2007-12-17
And unlike C++, Objective C is fully backwards compatible with C.

---

### Post by netkid91 on 2007-12-17
By the way, Objective GTK (libobgtk) is now on launchpad [https://launchpad.net/libobgtk](https://launchpad.net/libobgtk) .

---

### Post by kar-tar on 2008-01-08
There's a lot more nuance to object orientation than just being "object oriented."  C++ Multi-inheritance and Java Single-inheritance are different enough to cause different solutions to similar problems, and those are two of the most similar object systems.

Alan Kay (the inventor of Smalltalk -- on which Object C is based) said "Actually I made up the term "object-oriented", and I can tell you I did not have C++ in mind."  This would have been sometime in the 80s, around the same time he expressed the opinion that the only then popular languages that could really do OO were Smalltalk and Lisp.  I'm not sure which Lisp dialect he would have been referring to, but the Common Lisp object model is yet another Object system that is almost unrecognizable if you think of Object Orientation as a certain set of features from some other language you already know.

Similarly Javascript's (a really great little language that's just too verbose) prototype system is a really neat way of doing objects that doesn't immediately translate into C++.

The general opinion I've received from people who have done serious projects in both C++ / Java and Objective C / Smalltalk is that while C++ doesn't lack capabilities, its object system creates a tendency toward poor organization and inelegance.  This tendency can certainly be fought by a good team, but on the whole 100 Smalltalk projects will wind up in a prettier state than 100 C++ projects.  This of course ignores the fact that those 100 C++ projects will actually get finished because they have library and interop support that has been updated this decade.

---

### Post by H264 on 2008-02-04
Hey, we started a team on launchpad called Core Objectives, who's goal is to develop useful libraries/wrappers for the Objective-C language.

[https://launchpad.net/~coreobj]("https://launchpad.net/~coreobj")

Feel free to help out!
:popcorn:

---

