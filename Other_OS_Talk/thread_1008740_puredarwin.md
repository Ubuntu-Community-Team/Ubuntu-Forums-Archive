---
title: "puredarwin"
date: 2008-12-11
forum: Other OS Talk
---

### Post by luposolo on 2008-12-11
i have a few question how would i install gnome on puredarwin with the command line. puredarwin just comes with the core of the os, so thats why i want to install gnome. I'm thinking of making a distro out of this since there aren't many darwin distro's out there

---

### Post by zmjjmz on 2008-12-11
Am I to assume you want to make a binary OS X compatible OSS distro?
I would support you if I knew anything about OS X.
By the way, you won't be able to run applications like iMovie or iChat or iTunes.
Those depend on Apple's graphics layer, which is proprietary.

---

### Post by smartboyathome on 2008-12-12
> **zmjjmz said:**
> Am I to assume you want to make a binary OS X compatible OSS distro?
I would support you if I knew anything about OS X.
By the way, you won't be able to run applications like iMovie or iChat or iTunes.
Those depend on Apple's graphics layer, which is proprietary.

Actually, check out GNUstep. They've been working on creating an open version of the Cocoa toolkit as part of their stuff, so that things that use it could be run on non-Apple stuff.

---

### Post by cammin on 2008-12-12
[http://www.netbsd.org/docs/pkgsrc/platforms.html#darwin](http://www.netbsd.org/docs/pkgsrc/platforms.html#darwin)

No idea if it actually works, but it might be worth looking into.

---

### Post by 3rdalbum on 2008-12-12
> **smartboyathome said:**
> Actually, check out GNUstep. They've been working on creating an open version of the Cocoa toolkit as part of their stuff, so that things that use it could be run on non-Apple stuff.

I think the open-source Cocoa toolkit is for application developers who want to port their OS X applications to Linux. It doesn't emulate anything close to Mac OS X to get any binaries to run, and I don't believe that's their aim either.

---

### Post by Changturkey on 2008-12-12
Interesting..

---

### Post by zmjjmz on 2008-12-12
> **smartboyathome said:**
> Actually, check out GNUstep. They've been working on creating an open version of the Cocoa toolkit as part of their stuff, so that things that use it could be run on non-Apple stuff.

You would need Quartz too.
It's just nowhere near ready.

---

### Post by smartboyathome on 2008-12-12
> **zmjjmz said:**
> You would need Quartz too.
It's just nowhere near ready.

You're right, its not, but its at least a step towards OSX-Linux/Darwin compatibility, which someone can use to build further on.

---

### Post by luposolo on 2008-12-12
if you see here [http://www.puredarwin.org/screenshots](http://www.puredarwin.org/screenshots) he has fluxbox and Enlightenment running on puredarwin i would like to do that with gnome

---

### Post by smartboyathome on 2008-12-12
> **luposolo said:**
> if you see here [http://www.puredarwin.org/screenshots](http://www.puredarwin.org/screenshots) he has fluxbox and Enlightenment running on puredarwin i would like to do that with gnome

I think it uses GNU Darwin or MacPorts. Check out those two.

---

### Post by djhyland on 2008-12-13
Looks like NetBSD's pkgsrc works on Darwin ([[COLOR="Blue"]http://www.netbsd.org/docs/software/packages.html#platforms[/COLOR]]("http://www.netbsd.org/docs/software/packages.html#platforms")).  I took a look at the available packages, and it looks like Gnome 2.24.2 [[COLOR="Blue"]is available[/COLOR]]("ftp://ftp.netbsd.org/pub/pkgsrc/current/pkgsrc/README-all.html").

Note that I've never used Darwin or pkgsrc, so I can't guarantee that this will work.  I am, however, curious about this.  Let us know how it goes!

---

### Post by Sorivenul on 2008-12-13
> **djhyland said:**
> Looks like NetBSD's pkgsrc works on Darwin ([[COLOR="Blue"]http://www.netbsd.org/docs/software/packages.html#platforms[/COLOR]]("http://www.netbsd.org/docs/software/packages.html#platforms")).
NetBSD runs on just about anything (ask cardinals_fan for more details), so it's no surprise pkgsrc is supported on Darwin.

---

### Post by fistfullofroses on 2008-12-14
Very ambitious. I would recommend downloading the Darwin sources from Apple, and then proceeding to compile them using either Solaris or GNU/Linux as your build environment. A GNU/Darwin system would likely be your end result. You have already stated that you want to use GNOME, you therefore have to satisfy several dependencies (which are other GNU packages). Therefore, I would not only download the darwin sources, but refer back to Linux From Scratch for a small guide, also looking into BLFS. Good luck!

---

### Post by smartboyathome on 2008-12-14
> **fistfullofroses said:**
> Very ambitious. I would recommend downloading the Darwin sources from Apple, and then proceeding to compile them using either Solaris or GNU/Linux as your build environment. A GNU/Darwin system would likely be your end result. You have already stated that you want to use GNOME, you therefore have to satisfy several dependencies (which are other GNU packages). Therefore, I would not only download the darwin sources, but refer back to Linux From Scratch for a small guide, also looking into BLFS. Good luck!

You can't compile Darwin on Linux or Solaris, as there are differences between Apple's compiler and GNU's. Its made for Apple's compilers, which means unless you already have an Apple or Darwin, you can't compile it. Thats from what I have read, of course, and I could be completely wrong. :p

---

### Post by fistfullofroses on 2008-12-14
hmm... you may be right, but maybe not. Thinking about it, if the OS is written in C, it shouldn't matter. If, on the other hand, it is written in some strange and/or obscure language... you would certainly have problems. C is C, C++ is C++. You may need a few headers, but you certainly shouldn't have too much of problem. If special headers are needed, wouldn't they be released by Apple? Or is Apple's open source entrance just a farce?

---

### Post by djhyland on 2008-12-15
> **smartboyathome said:**
> You can't compile Darwin on Linux or Solaris, as there are differences between Apple's compiler and GNU's. Its made for Apple's compilers, which means unless you already have an Apple or Darwin, you can't compile it. Thats from what I have read, of course, and I could be completely wrong. :p

Last I checked, Apple still offers older versions of Darwin as binaries for both ppc and x86 architectures.  Perhaps one could use one of those to compile the newest version.

---

### Post by smartboyathome on 2008-12-15
> **djhyland said:**
> Last I checked, Apple still offers older versions of Darwin as binaries for both ppc and x86 architectures.  Perhaps one could use one of those to compile the newest version.

Thats true, I guess you could. :)

---

