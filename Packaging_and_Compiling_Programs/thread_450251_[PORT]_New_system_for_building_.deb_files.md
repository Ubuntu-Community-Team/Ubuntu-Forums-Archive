---
title: "[PORT] New system for building .deb files"
date: 2007-05-21
forum: Packaging and Compiling Programs
---

### Post by TimGws on 2007-05-21
The one thing that I like about Arch Linux and Frugalware, is the package management system, called "pacman". Along with pacman, is an application for compiling packages, called "makepkg". Makepkg is a very simplified system for creating packages.

With the help of checkinstall's sourcecode by my side, I have made a copy of makepkg, called " easypkg ", which instead of outputting .fpm files (like Frugalware's makepkg), it will output a .deb.

It is not perfect, and it is *VERY* hacked up.

Anyways, tell me what you think about it.

You can get it from [http://tim05.timg.ws/easypkg/easypkg-0.01.tar.bz2](http://tim05.timg.ws/easypkg/easypkg-0.01.tar.bz2)

NOTE: I have only made one .deb so far, but it has worked for me. I have not yet tried to make a split package (via Fsplit).

NOTE 2: The format of these files are just like PKGBUILD's from Arch Linux or FrugalBuild's from Frugalware.
[http://aur.archlinux.org](http://aur.archlinux.org) for some PKGBUILD's
[http://darcs.frugalware.org/repos/frugalware-current/source/](http://darcs.frugalware.org/repos/frugalware-current/source/) for some FrugalBuild's

NOTE 3: Best to use FrugalBuild's over PKGBUILD's :) .

---

### Post by pbw on 2007-05-21
This def sounds cool, as pacman is my package manager of choice. Both the AUR and pkgbuild structure/ABS are two things (among others) that make it impossible for me to leave Arch.

I'm not at home till tomorrow, but when i return i'll check it out, help test/tweak and let you know what I think TimGws. 

-- pbw

---

### Post by TimGws on 2007-05-21
Thanks pbw, It is very much appreciated. Allow me just to say, at the moment, you need to have the ezbuild (easypkg's "PKGBUILD") needs to be in the same folder as easypkg. This will soon not be the case, but it was just for testing :)

---

### Post by pbw on 2007-05-23
Hey Tim, sorry buddy. Was supposed to leave the gf's the other day. But i got screwed for a ride and here i am still lol. Took a quick peak anyways this morning. It's easy to strip out the fgrual addition eh,  just comment out the needs for the "ez" files?.. Anywhow, home tomorrow and i'll get a chance to test it out and actually check it out a bit more thorough ;).

-- pbw

---

### Post by TimGws on 2007-05-23
> **pbw said:**
> It's easy to strip out the fgrual addition eh,  just comment out the needs for the "ez" files?


Well, if you do not want any frugal stuff, then just rename your PKGBUILD ezbuild, and make it with:
```
ezmake -u
```
so it will not check if you are building the latest version of that package (another Frugal mod).

---

