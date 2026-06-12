---
title: "libc issues"
date: 2020-10-14
forum: Packaging and Compiling Programs
---

### Post by ognif on 2020-10-14
[COLOR=#242729][FONT=Arial]I developed a app for Ubuntu. I compiles it on Ubuntu 0.04 64bit with current dev-esentials. I created a package with CPack and sent to a friend. He got:

libm.so.6: version "GLIBC_2.29" not found
libc.so.6: version "GLIBC_2.27" not found
libm.so.6: version "GLIBC_2.29" not found
libc.do.6: version "GLIBC_2.28" not found

He is on Ubuntu 16. I have installed glibc 2.31 on my development machine. So I assume that this lib is missing on his Ubuntu 16? Can I add this to the package so a Ubuntu 16 user do have the needed libs available? Or do I have to compile it with something like a compatibility flag?[/FONT][/COLOR]

---

### Post by mc4man on 2020-10-14
If you want to produce a deb package for 16.04 then most cases inc. your case you have to build it on 16.04.

---

