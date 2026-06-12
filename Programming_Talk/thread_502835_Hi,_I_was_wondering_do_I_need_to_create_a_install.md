---
title: "Hi, I was wondering do I need to create a install"
date: 2007-07-17
forum: Programming Talk
---

### Post by dark joev on 2007-07-17
I have recently moved to linux becaues I wanted to make games for a system that wasn't on the mainstream and I have came from Windows and I was wondering do I need to make a install like is there a program to make .deb files or is there something I have to do in C++ or in any language I use make the .deb work I am use to using EXE and am not use to packages so please help




Thank you

---

### Post by mostwanted on 2007-07-17
Create a tar.gz source installer (configure script and Makefile does the work here). Install it using ./configure, make and checkinstall. This should create a deb file in the process of installing the program.

First learn how to use makefiles. Then creating other installers is quite easy.

---

### Post by dark joev on 2007-07-17
Ok thanks I was just a little confused with the process but I will look into it.

---

### Post by Carlos Santiago on 2007-07-17
A *.DEB file is an installer of a package of software (like *.MSI in windows) 

A *.DEB file is something like a compressed file that place the program files where they should be.

You can compile and run programs without the need to make a *.DEB package.  

DEB is the final step. Usually for the release version.

---

### Post by kknd on 2007-07-17
It's for linux only?

Then you can follow the suggestion of the other people, "native" packages are good.

Personally, I us IzPack to pack my Java apps, that keep them portable.

---

### Post by dark joev on 2007-07-17
I will more than likely be making both "native" only release and just general releases so thanks.

---

