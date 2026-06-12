---
title: "Carbon API for Linux?"
date: 2009-10-30
forum: Programming Talk
---

### Post by Pharaoh Atem on 2009-10-30
Hello,

I was looking at Wine the other day, and I noticed that Wine provides a way to compile Windows applications to Unix binaries, offering the ability to mix Unix and Win32 APIs to build applications.

Is there something similar for Carbon API users, to bring their applications to Linux? (Or maybe Cocoa, but not that quite so much...)

---

### Post by froggyswamp on 2009-10-30
I don't know, but I'd like to notice that a solution like Wine is perhaps the worst "type" of app for Linux. It's both (very) slow to startup and slow at execution, even Java is better.

---

### Post by winch on 2009-10-30
[http://en.wikipedia.org/wiki/GNUstep](http://en.wikipedia.org/wiki/GNUstep)

---

### Post by SunSpyda on 2009-10-31
GNUStep's based on OpenStep, which Cocoa also is 'from'. Carbon is just a toolkit to maintain compatibility with the old Macintosh Toolkit from the pre-OS X days.

If you want to build apps with Carbon, I don't think you will find a solution, if you wish to use the newer (and preferred) Cocoa, you will find that GNUstep will help you to compile it to Linux. Objective-C will be required.

---

### Post by nvteighen on 2009-10-31
I guess you're confusing Carbon (Mac OS Classic compatibility layer for Mac OS X) with Cocoa (Apple's implementation of OpenStep for Mac OS X; derived from NeXT's NeXTStep).

The GNU/Linux equivalent of Cocoa is GNUStep. That's a library only available for Objective-C and it's quite amazing but also a mess... even installing it (there are several packages, most are useless unless you want to use the GNUStep GUI toolkit) and compiling applications with it is a bit complicated... the steps described at the documentation are pretty unnecessary...

Also, GNUStep is a project with continuous delays and is really outdated in some stuff. Also gcc's Objective-C module is outdated as it doesn't support the language's last version (which adds automatic garbage collection... though GNUStep has a semiautomatic GC system).

---

### Post by slavik on 2009-10-31
Why and how did you think that WINE is anything like Java?

Also, using winelib for compiling windows apps is not a very good idea.

---

### Post by Pharaoh Atem on 2010-01-08
I was sort of hoping for a Carbon API binding to Linux, I have this huge program I wanted to recompile from Mac OS X Carbon to Linux, but obviously at this point that isn't possible.

The Carbon API is not a compatibility mechanism on Mac OS X. Carbon is Apple's increasingly deprecated C/C++ API (Apple is really pushing Cocoa) that was purposely abstracted enough so that Carbon apps could be recompiled from Mac OS 8 and 9 to Mac OS X. On Mac OS 9, the entire Carbon API is in a single file called CarbonLib, which abstracts away the underlying APIs that originally are part of Mac OS 9.

I hoped that there would have been a Carbon API binding for Linux, given the kind of opportunity it would bring to Linux to have some of the best Carbon apps available for Linux, such as Adobe Creative Suite (which are Carbon apps)...

---

