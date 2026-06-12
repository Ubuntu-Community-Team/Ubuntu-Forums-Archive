---
title: "apt-cache shows old version of cmake?"
date: 2013-02-05
forum: Packaging and Compiling Programs
---

### Post by rogerdpack on 2013-02-05
Hello.
With Precise, I am trying to get a newer version of "cmake":

[https://launchpad.net/ubuntu/+source/cmake](https://launchpad.net/ubuntu/+source/cmake) lists "2.8.10" as the latest.

$ sudo apt-get update
...
$ apt-cache show cmake
Package: cmake
Priority: optional
Section: devel
Installed-Size: 10446
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Modestas Vainius <modax@debian.org>
Architecture: amd64
Version: 2.8.7-0ubuntu5
...


am I doing something wrong? Any ideas why apt-cache would show a version that differs from launchpad here?
Thanks!
-roger-

---

### Post by mc4man on 2013-02-05
The .10 version is in raring, you're on precise

---

