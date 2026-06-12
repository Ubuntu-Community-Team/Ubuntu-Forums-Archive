---
title: "How to install 32 bit libraries on x86_64?"
date: 2011-05-11
forum: Packaging and Compiling Programs
---

### Post by dacha on 2011-05-11
Hi

1. How do I install a 32 bit library on an Natty x86_64 system? Some seem to be in ia32-libs, but what about the rest of them? In particular, libexpat seems to only have a 64 bit version.

2. How do I tell autotools to build in 32 bit? Setting CC="gcc -m32" seems to compile, but often doesn't link. Is something else necessary?

3. How do I tell the debian packaging tools such as pbuild to build in 32 bit?

Thank you

---

### Post by MadCow108 on 2011-05-11
> **dacha said:**
> Hi

1. How do I install a 32 bit library on an Natty x86_64 system? Some seem to be in ia32-libs, but what about the rest of them? In particular, libexpat seems to only have a 64 bit version.

in general you can't but expat has been converted to multiarch so you might have some luck with that:
[http://wiki.debian.org/Multiarch/Implementation](http://wiki.debian.org/Multiarch/Implementation)
But I do not recommend it yet, see the better solution now.

> 
2. How do I tell autotools to build in 32 bit? Setting CC="gcc -m32" seems to compile, but often doesn't link. Is something else necessary?

it probably won't link because the libraries its need are 64 bit.
> 
3. How do I tell the debian packaging tools such as pbuild to build in 32 bit?

Thank you
create a new chroot with 32 bit packages with --architecture or ARCH set to i386
```
pbuilder --create --architecture i386 ...
```
this will install all packages in their 64 bit variant and works fine on 64 bit machines, so its the best way to cross compile 32 bit applications until multiarch is fully there.

---

