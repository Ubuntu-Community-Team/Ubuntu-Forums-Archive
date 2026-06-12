---
title: "Problem Compiling Airsnort"
date: 2007-02-13
forum: Programming Talk
---

### Post by thomasmallen on 2007-02-13
I've downloaded Airsnort tar.gz files off of Sourceforge, and none of them will install once I extract their folders in /usr/bin/ and run ./configure from the Airsnort directory. I've tried various versions of 2.7 and even one 2.6, but each time I get the same error:

checking for C compiler default output... configure: C compiler cannot create executables
See'config.log' for more details.

So I go to config.log and see this (where the error is):

/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:2153: $? = 1
configure: failed program was:
| /* confdefs.h. */
|
| #define PACKAGE_NAME ""
(etc etc)

What am I doing wrong? If it's not me, how can I fix the problem file? Also, I poked all over the Airsnort directory and couldn't find any "confdefs.h"... I've received the same error I detailed above when logged in as myself (admin account) and even as Root, so it can't be permissions.

---

