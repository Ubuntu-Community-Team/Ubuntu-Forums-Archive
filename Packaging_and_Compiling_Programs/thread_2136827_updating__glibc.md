---
title: "updating  glibc"
date: 2013-04-18
forum: Packaging and Compiling Programs
---

### Post by sahar77 on 2013-04-18
Hi,

I want to install glibc with version higher than 2.28. using command: apt-get install glibc. but it tells me unable to locate package glibc.
can you tell me how can I install 2.28 version or higher ?

btway, I already have 2.15 version.
thanks!

---

### Post by Cheesehead on 2013-04-19
Replacing glibc without knowing exactly what you are doing can break your system.
Really, it's an important component. 2.17 is included in 13.04.

What makes you think you *need* version 2.28? As far as I can tell, that version does not seem to exist. According to [http://www.gnu.org/software/libc/](http://www.gnu.org/software/libc/) , 2.17 is the latest stable version.

---

### Post by sahar77 on 2013-04-19
wooW thak you so much for the heads up!

---

