---
title: "aria2c cross compile for android on ubuntu"
date: 2012-12-27
forum: Packaging and Compiling Programs
---

### Post by ankushkale1 on 2012-12-27
does anyone has experience of cross-compiling? I have android ndk r8c.
**Can anyone post simple scripts to cross compile aria2 for android on Ubuntu?**

ARIA2C requires statically compiled :

openssl
c-ares
expat libraries

link to aria2c : -> [https://github.com/tatsuhiro-t/aria2](https://github.com/tatsuhiro-t/aria2)

**i tried but didnt worked.. so if not scritps then atleast anyone please post statically compiled required libraries & headers so that i can try to build it.** ( Actually i tried to statically compile it with -static CFLAGS & --disable-shared --enable-static=yes  but still it requires some shared libs )
Actually I changed some files in source so that it will always retry on network failure( in which it normally aborts download)
Files are in  attachment.

---

