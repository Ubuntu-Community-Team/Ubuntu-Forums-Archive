---
title: "[SOLVED] K develop C, cant make"
date: 2008-08-11
forum: Programming Talk
---

### Post by Pocadotty on 2008-08-11
Hi, I am new to K develop, and am having programs building hello world.  When I try to build it prompts me telling me that the project doest have a make file, and when it tries to create one it fails... here is the output: 

cd '/home/pocadotty/mycode/dave' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -f Makefile.cvs && mkdir '/home/pocadotty/mycode/dave/debug' && cd '/home/pocadotty/mycode/dave/debug' && CFLAGS="-O0 -g3 " "/home/pocadotty/mycode/dave/configure" --enable-debug=full && cd '/home/pocadotty/mycode/dave/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -k 
aclocal
make: aclocal: Command not found
make: *** [all] Error 127
*** Exited with status: 2 ***

it looks like it needs a software package I don't have. Can someone tell me what I need to do to get it to build?

---

### Post by dwhitney67 on 2008-08-11
You probably have forgotten to install the development package:
```
$ sudo apt-get install build-essential
```

P.S.  If that fails, try with 'build-essentials'

---

### Post by Pocadotty on 2008-08-12
nope... I have build-essential, turns out it was that i didnt have automake... so i installed it, reconfigured the build, and it works great now.

---

