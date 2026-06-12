---
title: "Questions about deb packages"
date: 2005-07-27
forum: Packaging and Compiling Programs
---

### Post by foxy123 on 2005-07-27
I've got a couple of questions from a developer of quasar (an accounting programme). Since I consider myself a newbie, I would appreciate if anyone could give me some answers. Here they are:
> 1. Do .deb files include the source and get built from source or do they hold the files already compiled and to be installed?

2. Can one .deb file work on all the different Debian based systems or do I have to handle Gentoo, Ubuntu, ... 
cheers in advance....

---

### Post by Xian on 2005-07-27
1. The source is not included, if by source you mean the raw, uncompiled package. There are deb-src files available and perhaps this is what you are thinking about. For more information see the [Debian New Maintainer's Guide](http://www.debian.org/doc/manuals/maint-guide/index.en.html).

2. A single .deb file will not work on every Debian based system, in the same way that a .rpm file should not be installed on every RPM based environment. However, there are certainly some compatible distributions, and some .deb packages which are actually made to work on a variety of installations.

---

### Post by DJ_Max on 2005-07-27
Xian pretty much nailed everything. a .deb is fast to install because it's built from the source, and turned into a binary on someone else's system for you to use. A .deb denotes the Debian package format, and most of the time, will only work on the distro it was build on. For example, if I build something on a Debian computer, and give you the .deb on your Ubuntu system, it will probably install because you have the Debian package system, but you will probably run it problems, because Debian uses different software versions, ports, and that my package is build against.

---

