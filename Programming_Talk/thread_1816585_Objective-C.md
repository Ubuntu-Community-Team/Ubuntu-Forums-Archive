---
title: "Objective-C"
date: 2011-08-02
forum: Programming Talk
---

### Post by karlisba on 2011-08-02
Hi!
I know it is impossible to develop iPhone apps on other systems than Mac, but what about simple Obective-C and Cocoa code? I red then there is posibility to develop in Objective-C on windows and what about Linux Ubuntu, is there compilers for Objective-C and Cocoa?

---

### Post by Barrucadu on 2011-08-02
[http://en.wikipedia.org/wiki/GNUStep](http://en.wikipedia.org/wiki/GNUStep)

---

### Post by karlisba on 2011-08-02
O, thanks. :)

---

### Post by nvteighen on 2011-08-02
Objective-C in GNU/Linux is a bit disappointing...

1. GCC only supports Objective-C 1.0, i.e. no GC and less dynamic stuff to play with.
2. GNUStep is an (outdated) implementation of the OpenStep API, while Cocoa also adds stuff for OS X GUI development... If you want to know how horrible an OpenStep GUI (be it GNUStep or NeXTStep) looks like, follow this link: [http://en.wikipedia.org/wiki/File:OPENSTEP_Workspace_Manager.jpg](http://en.wikipedia.org/wiki/File:OPENSTEP_Workspace_Manager.jpg)

The fact is that ObjC has become more and more an Apple-specific programming language... IMO, due to the Free Software's community lack of serious attention.

---

