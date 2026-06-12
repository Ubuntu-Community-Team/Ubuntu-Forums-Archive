---
title: "[c++] iostream.h: No such file or directory"
date: 2011-11-14
forum: Programming Talk
---

### Post by rinosalman on 2011-11-14
hi...
i hope this is the correct forum to place my problem..
i'm being installing qt-x11-free.3.0.7, i use old version because the software that i will used, asked me to install this.
i ran ./ configure, and it worked, but when i continue with next step (ran make), i got this
"fatal error: iostream.h: No such file or directory compilation terminated"

i've did sudo apt-get install g++ and sudo apt-get install build-essential, but still doesn't worked...

help me please...i appreciate any help that can be given...

---

### Post by crdlb on 2011-11-15
Qt3 is still in the repos. Install libqt3-mt (and libqt3-mt-dev if you're compiling something against it).

---

### Post by Zugzwang on 2011-11-15
The problem you are having roots in the fact that the usage "iostream.h" is outdated. Once upon a time there were GCC versions where this was allowed.

There are two things you can try: First of all, you can try fixing the problem. Replace all "iostream.h" in every source code file by simply "iostream". However, this might not be the only change you have to apply to the code.

Second, you can try adding some packages to your system that provide some other versions of the iostream library. For example, you can install the "lsb-build-base3" package. Then, you need to tell your configure script to use an additional include directory, in this case "/usr/include/lsb3/c++/backward/". Run "./configure --help" in the directory of the program/library you are trying to compile to see how to do this.

Either way, you might have to apply some more fixes!

---

### Post by rinosalman on 2011-11-20
it worked...thanks

---

