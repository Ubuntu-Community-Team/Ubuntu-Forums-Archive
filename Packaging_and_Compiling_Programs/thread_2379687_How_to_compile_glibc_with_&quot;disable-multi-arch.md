---
title: "How to compile glibc with &quot;disable-multi-arch&quot; option on Ubuntu"
date: 2017-12-08
forum: Packaging and Compiling Programs
---

### Post by Virus666 on 2017-12-08
Hello,
  
I play **Enemy Territory: Quake Wars** on Ubuntu Mate;  unfortunately the game has some missing text characters due to outdated  dependencies. I found out that it is possible to fix the problem by  using multi-arch support disabled libc (x86) with LD_LIBRARY_PATH  variable.


  
[LIST]
[*][http://forums.warchest.com/showthread.php/32089-ETQW-oddities-with-glibc-2-15-FIX?p=396658&viewfull=1#post396658](http://forums.warchest.com/showthread.php/32089-ETQW-oddities-with-glibc-2-15-FIX?p=396658&viewfull=1#post396658) 
[*][http://forums.warchest.com/showthread.php/32089-ETQW-oddities-with-glibc-2-15-FIX?p=570552&viewfull=1#post570552](http://forums.warchest.com/showthread.php/32089-ETQW-oddities-with-glibc-2-15-FIX?p=570552&viewfull=1#post570552) 
[/LIST]
  
However, my Ubuntu Mate 17.10 installation requires glibc version  which exactly matches the system's own glibc. How can I compile glibc  with "disable-multi-arch" option on Ubuntu? Thank you!

  
My current glibc information:

```
$ sudo apt-cache show libc6
Package: libc6
Architecture: amd64
Version: 2.26-0ubuntu2
Multi-Arch: same
Priority: required
Section: libs
Source: glibc
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 11389
Depends: libgcc1
Suggests: glibc-doc, debconf | debconf-2.0, locales
Breaks: hurd (<< 1:0.5.git20140203-1), libtirpc1 (<< 0.2.3), locales (<< 2.26), locales-all (<< 2.26), nscd (<< 2.26)
Replaces: libc6-amd64
Filename: pool/main/g/glibc/libc6_2.26-0ubuntu2_amd64.deb
Size: 2777762
MD5sum: f33ebbfb177b9e072fec0ab07d480dbe
SHA1: 2887712cd26956310e65a1a481ea0007bb87f505
SHA256: d42d424e72a9059bd00a89445d1af319caa4aee5eaf8f80636b2b3117ea475b3
Homepage: http://www.gnu.org/software/libc/libc.html
Description-en: GNU C Library: Shared libraries
 Contains the standard libraries that are used by nearly all programs on
 the system. This package includes shared versions of the standard C library
 and the standard math library, as well as many others.
Description-md5: fc3001b0b90a1c8e6690b283a619d57f
Task: minimal
Supported: 9m
```

```
$ LC_ALL=C ldd --version
ldd (Ubuntu GLIBC 2.26-0ubuntu2) 2.26
Copyright (C) 2017 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
Written by Roland McGrath and Ulrich Drepper.
```

```
$ /lib32/libc.so.6
GNU C Library (Ubuntu GLIBC 2.26-0ubuntu2) stable release version 2.26, by Roland McGrath et al.
Copyright (C) 2017 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.
Compiled by GNU CC version 6.4.0 20171010.
Available extensions:
    crypt add-on version 2.1 by Michael Glad and others
    GNU Libidn by Simon Josefsson
    Native POSIX Threads Library by Ulrich Drepper et al
    BIND-8.2.3-T5B
libc ABIs: UNIQUE IFUNC
For bug reporting instructions, please see:
<https://bugs.launchpad.net/ubuntu/+source/glibc/+bugs>.
```


Regards.

---

