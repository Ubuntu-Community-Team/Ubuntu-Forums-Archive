---
title: "Can't find sys2.h from coreutils!"
date: 2008-01-12
forum: Programming Talk
---

### Post by mexpolk on 2008-01-12
I'm new to Linux C programming, and I'm trying to implement case_GETOPT_VERSION_CHAR and case_GETOPT_HELP_CHAR macros. These two are in sys2.h from "coreutils"....

My question is: Is there any package that brings header files from coreutils? (ie. sys2.h) what path they're placed? or is the right thing to do just downloading coreutils sources and use them?

Thanks!

---

### Post by geraldm on 2008-01-12
You  can google for sys2.h and get some results.
It was present, then removed from some of the results, 
Found in some older *BSD code.
Also mentioned as possibly found in fileutils-4.1.

It is not in coreutils-6.9 package
coreutils package installs no headers.
My guess is that the source you are working with has some bad token pasting in coreutils-6.9/sys/system.h or other files in that directory.

Gerald

---

### Post by mexpolk on 2008-01-15
It seems to be gone (sys2.h)!
I couldn't find header files so I'm going to implement my own macros.

Thanks for your reply Gerald!

---

