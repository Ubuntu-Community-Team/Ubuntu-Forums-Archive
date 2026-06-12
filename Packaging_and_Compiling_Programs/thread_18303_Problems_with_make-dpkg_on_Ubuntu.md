---
title: "Problems with make-dpkg on Ubuntu"
date: 2005-03-05
forum: Packaging and Compiling Programs
---

### Post by Kaizoku on 2005-03-05
First I apologize for my bad english

Second, I got a problem in the installation of a module I do myself with debian tools ( make-kpkg)

and when I try to install it it says that he depends of kernel-image
but I don't have install kernel-image, I install linux-image from ubuntu.
I find nothing about the kernel's name in make-dpkg
I try to use -force-all on the .deb file but it does nothing (my .deb is broken)


How can I reslove it? I find nothing about changing depends in .deb
I thought to build an ampty .deb that depends on linux-image-{version} and create a kernel-image-{version}
I don't want to rebuild my kernel.
How can I do?

---

### Post by az on 2005-03-05
"and when I try to install it it says that he depends of kernel-image"

What package do you mean?  the kernel-package package does not depend on kernel-image.  It does not even depend on a linux-image.  It is in Main.  Are you using sources other than Ubuntu repositories?


"but I don't have install kernel-image, I install linux-image from ubuntu.
I find nothing about the kernel's name in make-dpkg"

uname -a
the packages in Ubuntu are named linux-image-2.6.8.1-4-284 and linux-source-2.6.  Kernel-image-2.6.8-2 are Debian packages.  Do not use them.

"I try to use -force-all on the .deb file but it does nothing (my .deb is broken)"
Do not ever do that.  There is never a good reason to do this.  Remove the offending package.

---

### Post by Kaizoku on 2005-03-06
Still sorry for bad english
I try to install fuse-source, it is the source for a module
so to install it in a debian way, I used make-kpkg method, as said here [http://www.advogato.org/person/robertc/diary.html?start=30](http://www.advogato.org/person/robertc/diary.html?start=30)
but the problem is that make-kpkg create a depends on kernel-image not linux-image

How to create module in Ubuntu? The ubuntu wiki explain for kernel-image not linux-image.

---

### Post by Kaizoku on 2005-03-06
I found the solution, all I have to do is edit the file in debian directory and replace kernel-image by linux-image

---

