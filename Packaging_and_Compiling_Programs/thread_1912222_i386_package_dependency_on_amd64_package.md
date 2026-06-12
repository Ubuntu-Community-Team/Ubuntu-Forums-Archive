---
title: "i386 package dependency on amd64 package?"
date: 2012-01-20
forum: Packaging and Compiling Programs
---

### Post by eyelessfade on 2012-01-20
I need to create a package with a dependency on two i386 library for amd64.

It's to be able to run proprietary x86-binary code on x86_64 computers.

is it possibly to specify it in the control file?

---

### Post by MadCow108 on 2012-01-20
its possible if the library packages have been multiarched and the target distribution is >= natty
The syntax is then package-name:architecture

if it has not been multiarched and it is not in ia32libs you're out of luck. you have to package the libraries appropriatly yourself.

see:
[http://wiki.debian.org/Multiarch/Implementation](http://wiki.debian.org/Multiarch/Implementation)
[https://wiki.ubuntu.com/MultiarchSpec](https://wiki.ubuntu.com/MultiarchSpec)

---

### Post by eyelessfade on 2012-01-23
The problem is not that they don't exist. they do, but I want them to be a dependency of my amd64 .deb package.

In witch case I get the following error when trying to compile the deb file.
```
dpkg-deb: error: parsing file 'myPackage/DEBIAN/control' near line 7 package 'myPackage':
 'Depends' field, reference to 'libxml2': invalid architecture name 'i386': a value different from 'any' is currently not allowed

```

---

### Post by MadCow108 on 2012-01-23
if it has a i386 dependency, it must be 32 bit code.
just make a i386 package + Multiarch: foreign or same depending on what it is.
then you can install it on amd64 systems.

---

