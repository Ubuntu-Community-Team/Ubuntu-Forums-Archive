---
title: "Gcc options while compiling for .deb packages?"
date: 2010-12-12
forum: Packaging and Compiling Programs
---

### Post by zeiaar on 2010-12-12
Hi,

what gcc (or g++ more precisely) options should I be using when compiling software to be put in .deb packages? So, to be sure that the compiler isn't using any optimisations specific only to the current (compilation time) architecture.

Currently I'm using these:
For amd64: "[FONT="Courier New"]-m64 -march=x86-64 -O3[/FONT]"
For i386:  "[FONT="Courier New"]-m32 -O3[/FONT]"

I thought that those should be fine but I got feedback that my program is crashing on another machine with "Illegal instruction" message. (That was from the 32bit version, compiled under VirtualBox guest.)

BTW, if someone else wants to make a try, my ZoomPanViewer project is hosted here:
[http://code.google.com/p/zoompanviewer/]("http://code.google.com/p/zoompanviewer/")

- Juuso

---

### Post by SevenMachines on 2010-12-12
Hi. i'd make a guess that the virtualbox processor that is emulated has an instruction set that is greater than whatever processor the bug is happening on. Could be something else but you tend to see things like "illegal instruction" when running for example, a program compiled for i686 and running on i386, that kind of thing anyway.
A build log on virtual box and a gdb backtrace of the bug might shine some light on it but you might try cross compiling on your 'real' computer rather than virtualbox and see if the problem still happens.
Generally i'd use pbuilder to build debianized source in a target environment to do this but i'm guessing someone else will know an easy way to set up a good cross building environment for compilation alone?...

---

### Post by zeiaar on 2010-12-12
Hi, thanks for the reply! Yep, I think that you are somewhat on-a-right-track.. The virtual machine really told me that it was i686 (from "uname -m")...

Yes, I'm quite sure that pbuilder etc tools are useful, but I would still like to learn the manual way first (and because my source isn't fully debianized yet)... And I think that it should be possible as those tools must be using gcc/g++ under-the-hood anyway... So, I still think that **there must be a simple way for forcing gcc to use only the "standardized" i386 instruction set, without need for setting up a real cross-compilation environment... Correct?**

- Juuso

PS. Could somebody tell me whether the 64-bit version (downloadable [here]("http://code.google.com/p/zoompanviewer/downloads/list")) of my fancy (:P) image viewer works either... Thank you!

> **SevenMachines said:**
> Hi. i'd make a guess that the virtualbox processor that is emulated has an instruction set that is greater than whatever processor the bug is happening on. Could be something else but you tend to see things like "illegal instruction" when running for example, a program compiled for i686 and running on i386, that kind of thing anyway.
A build log on virtual box and a gdb backtrace of the bug might shine some light on it but you might try cross compiling on your 'real' computer rather than virtualbox and see if the problem still happens.
Generally i'd use pbuilder to build debianized source in a target environment to do this but i'm guessing someone else will know an easy way to set up a good cross building environment for compilation alone?...

---

### Post by SevenMachines on 2010-12-12
Yep, i only mentioned pbuilder because it makes cross compilation simple, especially when using 32bit libraries in amd64 when the libraries arent available as lib32* cross compiling libraries in the amd64 repositories. Some sort of chroot environment would be the non debian packaging equivalent i suppose.

To be honest, i thought -march=i386 ensured that only i386 compatible machine code was used? Maybe i'm wrong on that but even the -m32 option..
man gcc:
> -m32:
...The 32-bit environment sets int, long and pointer to 32 bits
           and generates code that runs on any i386 systemYou might want to check what command line g++ is actually using when it builds on virtualbox, maybe it gets some unwanted options from environment variables or something.

There is of course also a chance something else is happening, some sort of stack corruption or something, without a backtrace it'd be a chore to check though

---

### Post by zeiaar on 2010-12-12
Yep, I think that I need to get in touch with the other machine myself to solve this out.. to see if the problem really comes from architecture dependant compilation or are there some other problems with my app...

---

### Post by zeiaar on 2010-12-18
Hah! This turned out to be just as stupid error as one can image... I used some statically linked libraries within my program and those libraries had been compiled separately with [FONT="Courier New"]-march=native[/FONT]. :P

So, it seems that those [FONT="Courier New"]-m32[/FONT] and [FONT="Courier New"]-m64[/FONT] flags should really be enough for making portable compilations.

As a consequence, the .debs available [here]("http://code.google.com/p/zoompanviewer/downloads/list") should be working now! ;)

---

