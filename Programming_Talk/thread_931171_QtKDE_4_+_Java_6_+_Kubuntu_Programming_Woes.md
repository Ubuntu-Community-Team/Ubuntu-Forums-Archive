---
title: "Qt/KDE 4 + Java 6 + Kubuntu Programming Woes"
date: 2008-09-27
forum: Programming Talk
---

### Post by Xanderfoxx on 2008-09-27
I see that there does not seem to be a relatively easy way to start coding in Java.  I know this has been said before, but I love Java, just hate Swing and AWT. Ugly and last-resort-type. (no flaming, you won't sway me.)  I'm hoping to use Qt 4, as apps written for it look great in both KDE 4 and GNOME.  Is there a book or list of resources that one of you geniuses could recommend, so I can be a Qt/KDE 4 coder, as well as a Java coder.  What I've found so far:  Apparently, there is little obvious support for Java in Qt 4, and the wrappers to JNI are minimal, but they work well enough for some uses. (Therefore I can start experimenting with them, and get familiar.)  KDE 4 is supposed to be platform-independent, which I think is the most brilliant thing they've ever done (Who wouldn't want KDE everywhere?? Or GNOME for that matter??) Some people think that porting Linux apps to Windows is bad because supposedly people will think, "Oh, I can get those apps on Windows. what do I need Linux for?" NO! They will more likely think, "I can get these awesome apps like Amarok, K3B, Kopete, and KOffice on Linux, which is bug-, spyware-, virus-, and relatively cost-free! what do I need Winblows for"  That's exactly what I would think, and I don't think many people would require much to see it that way, either.  Ahem! Anyway, I'm hoping that you guys may be able to shed some light on the whole KDE-Java business.  Arigato gozaimasu!

---

### Post by gorilla on 2008-09-27
I'm not quite sure what you actually want to know.. :)
..however:
There actually is good Java support from Qt, it's called Qt Jambi. That is a set of Java bindinghs for Qt, so you don't have to wiggle around with JNI.
To my knowledge there are no KDE4 bindings for Java yet unfortunately.
About books: I thinnk "C++ GUI Programming wit' Qt4" by Jasmin Blanchette and Mark Summerfield is good.

---

### Post by Xanderfoxx on 2008-09-27
> **gorilla said:**
> I'm not quite sure what you actually want to know.. :)


Well, I would like community input on general development tips, sites and books that would be of use (I don't mind spending money.)

> **gorilla said:**
> 
There actually is good Java support from Qt, it's called Qt Jambi.


Cool. I'll take a look at that. (Though, last time I looked, they didn't have a Javadoc or something I could find that documented the methods, classes, and templates I should use to develop KApplications.

> **gorilla said:**
> 
 That is a set of Java bindings for Qt, so you don't have to wiggle around with JNI.
To my knowledge there are no KDE4 bindings for Java yet unfortunately.


Shuckydarn! Oh, well. I'll have to wait until it comes out of beta, then. Arg.

> **gorilla said:**
> 
About books: I think "C++ GUI Programming wit' Qt4" by Jasmin Blanchette and Mark Summerfield is good.

That would be great, but that would mean I would have to learn C/C++, wouldn't it? I don't know that yet. It'll take awhile to get that under my belt.

It is true that I need to learn C/C++, Python (or similar), PHP, Assembly, and BASH, but I was hoping I could use Jambi for KDE 4 without having to first learn C/C++.

Thanks. Anything else?

---

### Post by gorilla on 2008-09-28
> **Xanderfoxx said:**
> Well, I would like community input on general development tips, sites and books that would be of use (I don't mind spending money.)
I just couldn't figure out at which aspects of development you want input. Java or Qt or both?


> Cool. I'll take a look at that. (Though, last time I looked, they didn't have a Javadoc or something I could find that documented the methods, classes, and templates I should use to develop KApplications.
Just look aroud at the Trolltech site, documentation is pretty good, there are also some tutorials to walk through. 


> Shuckydarn! Oh, well. I'll have to wait until it comes out of beta, then. Arg.
KDE4 is already out of beta ;)
Unfortunately it seems there simply is nobody at the moment who wants to do it. At least that is the last thing I have heard- nobody's working on it :(


> That would be great, but that would mean I would have to learn C/C++, wouldn't it? I don't know that yet. It'll take awhile to get that under my belt.

It is true that I need to learn C/C++, Python (or similar), PHP, Assembly, and BASH, but I was hoping I could use Jambi for KDE 4 without having to first learn C/C++.

I don't know of any Jambi books out there. It's all for c++. That doesn't matter much though, if you know Java you can mostly read and understand Qt books without knowing c++. If you neither know Java nor c++ you'll struggle though.
Using the Qt library is not all that diffrent from c++, java or python. After all its always the same library.
Just go through the Qt Jambi tutorials at Trolltech's site to get a basic feel.
Have a look at the dokumentation. Every class and method has a javadoc. Code snippets within the doc are c++ though.
Google for Qt4 tutorials, there are a few out there. Take care tutorials are for Qt4, not Qt3.

---

