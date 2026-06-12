---
title: "Kernel Development on Ubuntu"
date: 2007-08-07
forum: Programming Talk
---

### Post by spookware on 2007-08-07
Hello everyone I am looking for some advice.

First a bit about me so you can get some context. I am an expert  kernel and low level system software developer for the Windows platform. I am getting in to kernel development for linux in my spare time. I have dabbled in it for a few years now. I have read every book on the subject that is available. OK so the context is out of the way... on to the question.

I have read the tutorials on compiling custom kernels for ubuntu. I have built custom kernels myself on several occasions. What I want to do is step up the production level of my development work flow so that my testing boxes are not just a cobbled together hacks with various patches and manual configuration cruft all over the place.

Currently when I am messing with a kernel on a testing computer I end up doing all sorts of stuff that mess with the underlying stuff that when I want to roll back I have to ghost the system.

What I am interested in is learning how to better integrate my code in to ubuntu. 
For example one thing I am not clear on is just what is considered best practices for version numbers of kernel-package produced debs.

I have read all of the debian development guides so I know how to make packages but the kernel packages seem to be somewhat special. Does anyone know of a documentation source that explains them.

Or how I can compile the restricted drivers (particularly nvidia) against my own custom kernels and get them in to packages.

finally any advice on tools to build out of tree modules and turn them in to packages. 

Basically any advice on how to better integrate my own development tool chain to integrate with ubuntu would be ideal. I currently use linux from scratch and hand cobbled scripts to manage all this stuff. I would much rather use Ubuntu as a starting place for this purpose.

Thanks, and sorry the sort of nebulous questions but if I new what I was looking for I would not have to ask as I can Google with the best of them.

---

### Post by pmasiar on 2007-08-07
I would recommend to start with becoming a [MOTU](https://wiki.ubuntu.com/MOTU) - Master Of The Universe. They have mentors and school, will teach you how to build ubuntu packages you maintain. After learning maintainer tools, pick a project you like (and you will become knowledgeable about a few as MOTU), and go upstream, help with development.

---

### Post by spookware on 2007-08-08
Thanks for the tip  but I do not think that will help me. Maintainning user mode software packages is not to hard. I can easily handle that and know how it works.

This sort of highlights what I am getting at. Standard packages in the universie are not to hard to build and maintain. Hell, if the program in question is built with auto-tools it is almost trivial.

However my interest is in kernel, kernel modules, and low level system software like glibc, etc..

The debs for this stuff seem rather special (particularly the kernel) and what I am not clear on is how to build all these sort of "base" packages from my own source tree's.

I would be happy to join up with the MOTU if I knew of a project that worked on this type of stuff but from what I can tell these types of packages are part of ubuntu proper and are not handled by the universe maintainers.

However I might be able to learn something from a project in the universe that deals with out of tree kernel modules. Does anyone know of such a project?

Thanks again.

---

### Post by eentonig on 2007-08-08
Maybe you could try to contact Canonical directly? I'm sure they'll be more then happy with someone that can be usefull in kernel(module) devellopment. Not?

---

### Post by tseliot on 2007-08-08
> **spookware said:**
> Or how I can compile the restricted drivers (particularly nvidia) against my own custom kernels and get them in to packages.
Ubuntu has its own scripts to build the restricted modules and kernels. It's a package whose source code you can get by typing:
```
apt-get source linux-restricted-modules-generic
```

You will have to study the source code (e.g. its debian/rules) and see how it works since I don't think it's documented. Fortunately the code is commented.

---

### Post by pmasiar on 2007-08-08
> **spookware said:**
> I would be happy to join up with the MOTU if I knew of a project that worked on this type of stuff but from what I can tell these types of packages are part of ubuntu proper and are not handled by the universe maintainers.

Why don't you ask MOTU? *someone* has to maintain the kernel code! 

I doubt many MOTU hackers are around here (tseliot is the only one). MOTU gurus correctly don't waste time to answer simple questions posted in this forum (people with far less skils, like me, can do that :-) )

---

### Post by tseliot on 2007-08-08
> **pmasiar said:**
> Why don't you ask MOTU? *someone* has to maintain the kernel code! 

I doubt many MOTU hackers are around here (tseliot is the only one). MOTU gurus correctly don't waste time to answer simple questions posted in this forum (people with far less skils, like me, can do that :-) )
I think the kernel team deals with that package.

BTW I'm not a MOTU... yet ;)

---

### Post by spookware on 2007-08-08
> **tseliot said:**
> Ubuntu has its own scripts to build the restricted modules and kernels. ...
You will have to study the source code (e.g. its debian/rules) and see how it works since I don't think it's documented. Fortunately the code is commented.

Thanks. I have allready been over that package with a fine tooth comb. I was lead there after reading this wiki entery

[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)

I am still trying to get my head around the new "ubuntu" ways of doing things as opposed to the old "debian" way of doing kernels.

What I am interested in is basically all the stuff that should be on that page that is not. ie. best practices on versioning (the AUTOBUILD=1 stuff with the uuidgen thing stinks). Hopeing there is a better way so that I can keep my own version number system alongside the ubuntu system, just like the old debian way used to work. It is a pain keeping a mapping from uuid to my internal version numbers so that I can figure out which versin I am testing. As a mere mortal I have a hard time remember uuids off the top of my head :)

Or how to integrate and out of tree module in to the build system. That one I am completely lost on. I have tried to read through all the build scripts but I am at a loss as to how I can hook in to all that from outside the tree. If it is even possible?

integrating external modules in to initramfs is really troublesome. 

I guess maybe ubuntu just isn't what I am looking for. I mean on that page they sure go out of the way to try and convince you not to mess with the kernel image. I have been meaning to check out rpath rbuilder to see if that might meet my needs better. Does anyone here have any expirience with that?

---

### Post by tseliot on 2007-08-09
> **spookware said:**
> I guess maybe ubuntu just isn't what I am looking for. I mean on that page they sure go out of the way to try and convince you not to mess with the kernel image. I have been meaning to check out rpath rbuilder to see if that might meet my needs better. Does anyone here have any expirience with that?
Maybe you should try asking on #ubuntu-devel on freenode

---

