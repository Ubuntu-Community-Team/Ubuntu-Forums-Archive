---
title: "Compile a MacOS X10 code source on ubuntu"
date: 2010-04-02
forum: Packaging and Compiling Programs
---

### Post by pkhetan on 2010-04-02
Hi,

I just wonder if i can compile a program in my UBUNTU 9.10 from a code source that was originally for a MacOS  X10.5.

the program is OsiriX and the code source is at :
[http://osirix.svn.sourceforge.net/viewvc/osirix/Documentation/Guides/Development/index.html](http://osirix.svn.sourceforge.net/viewvc/osirix/Documentation/Guides/Development/index.html)

Appreciating your help

---

### Post by Bachstelze on 2010-04-02
Apparently the program uses Cocoa, which is an Apple proprietary, OS X-only framework. So no, it won't work on Linux or any other OS besides OS X.

---

### Post by wmcbrine on 2010-04-02
Some Cocoa apps will build with GNUstep.

---

### Post by Vorian on 2010-04-02
actually, it might just work with build-essential.

I find [http://packages.ubuntu.com/](http://packages.ubuntu.com/) very useful when I'm looking for dependencies.

---

### Post by pkhetan on 2010-04-03
> **Vorian said:**
> actually, it might just work with build-essential.

I find [http://packages.ubuntu.com/](http://packages.ubuntu.com/) very useful when I'm looking for dependencies.

Can you give more detail about how to use build-essential. I'm not a programmer, i'm only a person who like playing with the depth of a computer but my knowledge has limit. I know only that to compile an application under UBUNTU, i have to run make, make install :rolleyes:
I'm very interested in that application (OSIRIX) because it's very useful in my work (orthodontist)

Thanks

---

### Post by wmcbrine on 2010-04-03
"bulid-essential" isn't something you use, just something you install, that gets you the standard build tools. If you're running "make", you probably already have it.

I think it's very unlikely that a Cocoa app will build with just build-essential.

---

