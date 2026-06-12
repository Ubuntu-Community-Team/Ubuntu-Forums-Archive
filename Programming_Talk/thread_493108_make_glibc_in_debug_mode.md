---
title: "make glibc in debug mode"
date: 2007-07-05
forum: Programming Talk
---

### Post by mbuchoff on 2007-07-05
Hi all.  I'm new to this forum (and Linux pretty much).

I am currently  working on the XBMC open source project.  After running our software in Valgrind, I discovered that glibc's dlopen function has a memory leak.  Although I have very little Linux experience, I have been a programmer for several years and would like to try my luck at this bug.

In order to fix this issue, I want to compile glibc in debug mode so that Valgrind can tell me exactly where the leak is and I can (try to) fix it.  Can anyone give me some instruction on how to do this?  According to glibc's help page, glibc changes slightly with each Linux distribution and so I should ask my questions here first.

Thanks in advance.

Michael Buchoff

---

### Post by duff on 2007-07-05
Try installing "libc6-dbg" first.  That'll give you the debugging symbols you're after.

---

### Post by mbuchoff on 2007-07-05
Thanks for the help.  Although certain errors are now more well-defined, those involving libc-2.5.so are still pretty cryptic.  Do you know of any thing else I can try?

---

