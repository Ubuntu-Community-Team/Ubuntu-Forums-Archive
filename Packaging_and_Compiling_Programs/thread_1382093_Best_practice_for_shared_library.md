---
title: "Best practice for shared library"
date: 2010-01-15
forum: Packaging and Compiling Programs
---

### Post by Creat on 2010-01-15
Hi,

I'm trying to build my first packages using the source code written by someone else (and released under the GPL). The first one is a shared library (let's call it libfoo). The second one is a software that requires this shared library (let's call it bar).

With the default configure and make files, when I package libfoo, the library gets installed in /usr/lib/libfoo however, the other package (bar) that needs it looks for it in /usr/lib.

As I am really new to this I am wondering what the practices are. In particular, where should the shared library be stored (/usr/lib/libfoo or /usr/lib)? If it's in /usr/lib/libfoo, what's the best way to have a copy in /usr/lib? Is it best to symlink or to copy the file? Alternatively, is it something that I need to specify in the configure or make files?

I hope I'm being clear enough... please let me know if you need additional information to help solve this problem.

Thanks!

---

### Post by SevenMachines on 2010-01-15
i think policy is that libraries go in /usr/lib and support files for the library go in subdirectories like /usr/lib/foo. not 100% but see
[http://www.debian.org/doc/debian-policy/ch-sharedlibs.html](http://www.debian.org/doc/debian-policy/ch-sharedlibs.html)

---

