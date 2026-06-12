---
title: "Compilers comparison: GCC vs open64"
date: 2012-02-12
forum: Programming Talk
---

### Post by erotavlas on 2012-02-12
Hi all,

I have some question about the compilers GCC and open64.
1) Which gets better performance?
2) Is open64 really open or it works well only with AMD processors?

I'm not expert about the advanced configuring of GCC, but I know that the autoparallel options (graphite framework [https://accounts.google.com/ServiceLogin?service=groups2&passive=1209600&continue=http://groups.google.com/group/gcc-graphite&followup=http://groups.google.com/group/gcc-graphite](https://accounts.google.com/ServiceLogin?service=groups2&passive=1209600&continue=http://groups.google.com/group/gcc-graphite&followup=http://groups.google.com/group/gcc-graphite)) don't work very well and they need an enhancements. So I would like to get the best performance from the my CPU: do you know if exist a guide of tuning GCC (except this one [http://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html](http://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html)).

Thank you

Salvatore

---

### Post by 3Miro on 2012-02-12
Open64 is distributed under GPLv2, same as the Linux kernel. Open64 is as "open" (in the sense of Free Open Source Software) as it can get.

Here are some benchmarks, which give that gcc is overall better. I am not sure how reliable those benchmarks are (also they are done on AMD's Opteron CPUs).

[http://www.phoronix.com/scan.php?page=article&item=llvm3_gcc_open64&num=1](http://www.phoronix.com/scan.php?page=article&item=llvm3_gcc_open64&num=1)

All of Ubuntu, from the kernel to Xorg to Unity to Firefox, all of it is compiled with gcc. GCC cannot be significantly weaker. Maybe Open64 is better for some specific purpose, but in general I would go with gcc.

---

### Post by erotavlas on 2012-02-12
> **3Miro said:**
> Open64 is distributed under GPLv2, same as the Linux kernel. Open64 is as "open" (in the sense of Free Open Source Software) as it can get.

Here are some benchmarks, which give that gcc is overall better. I am not sure how reliable those benchmarks are (also they are done on AMD's Opteron CPUs).

[http://www.phoronix.com/scan.php?page=article&item=llvm3_gcc_open64&num=1](http://www.phoronix.com/scan.php?page=article&item=llvm3_gcc_open64&num=1)

All of Ubuntu, from the kernel to Xorg to Unity to Firefox, all of it is compiled with gcc. GCC cannot be significantly weaker. Maybe Open64 is better for some specific purpose, but in general I would go with gcc.

Thank you for your fast reply. What about the other question? How to optimize GCC?
I know that the autoparallel options (graphite framework [https://accounts.google.com/ServiceL...p/gcc-graphite]("https://accounts.google.com/ServiceLogin?service=groups2&passive=1209600&continue=http://groups.google.com/group/gcc-graphite&followup=http://groups.google.com/group/gcc-graphite"))  don't work very well and they need an enhancements. So I would like to  get the best performance from the my CPU: do you know if exist a guide  of tuning GCC (except this one [http://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html](http://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html)).

---

### Post by 3Miro on 2012-02-12
That's pretty much the official documentation about the GCC options. A few years ago I was looking into optimization and AMD had their own guide that gave a list of options that they consider optimal. I am sure Intel has something similar somewhere.

The main options are:
-O2 (standard)
-O3 (faster, but a bit risky depending on the situation)
-march=native (this one works automatically for gcc to enable/disable options)

---

### Post by MadCow108 on 2012-02-12
how about just trying them both?
thats the only way to find out which one is better for your code.
Some code may be faster when compiled with open64 other with gcc.

make sure to use the correct march option (= march=native in newer versions) and enable similar options, e.g. the link-time optimizer (off by default), autovectorizer (on with -O3) and autoparallizer (off by default)
also use up to date versions, gcc 4.6 and 4.7 have made large improvements to the autovectorizer and link-time-optimizer

---

### Post by erotavlas on 2012-02-14
Hi all,

I have found this guide [http://developer.amd.com/Assets/CompilerOptQuickRef-61004100.pdf](http://developer.amd.com/Assets/CompilerOptQuickRef-61004100.pdf) on ufficial AMD website. I'm compiling with GCC 4.6.2 and I would like to know if the parameters specified in guide are the best or I can add other parameters like the following example:

from the guide
-O3 -march=barcelona -fschedule-insns -fschedule-insns2 -fsched-pressure -funroll-all-loops -fprefetch-loop-arrays --param prefetch-latency=300 -minline-all-stringops -fno-tree-pre -ftree-vectorize

additional parameters
Compiler
-O3 -fwhole-program -flto -fsplit-stack -march=barcelona -fschedule-insns -fschedule-insns2 -fsched-pressure -funroll-all-loops -fprefetch-loop-arrays --param prefetch-latency=300 -minline-all-stringops -fno-tree-pre -ftree-vectorize
Linker
-flto

P.S. the autoparallizer is not completed as you can read here graphite framework [http://groups.google.com/group/gcc-graphite/browse_thread/thread/71a404e89cfe36b8](http://groups.google.com/group/gcc-graphite/browse_thread/thread/71a404e89cfe36b8)

Thank you

---

### Post by qeemat on 2012-02-17
Actually, Open64 produces better code than gcc.
Open64 is programmed in C++, while gcc is programmed in C.
Open64 is not as maintained as gcc.
gcc has more backends compared to Open64.
The gcc comunity is larger, but this is not a quality criteria.
One advantage that gcc has over open64 is the variety of architecures
especially embedded ones that it supports if that is what you are
interested. Perhaps somebody can add to if open64 does that as well.Actually, Open64 produces better code than gcc.

---

### Post by erotavlas on 2012-02-17
> **qeemat said:**
> Actually, Open64 produces better code than gcc.
Open64 is programmed in C++, while gcc is programmed in C.
Open64 is not as maintained as gcc.
gcc has more backends compared to Open64.
The gcc comunity is larger, but this is not a quality criteria.
One advantage that gcc has over open64 is the variety of architecures
especially embedded ones that it supports if that is what you are
interested. Perhaps somebody can add to if open64 does that as well.Actually, Open64 produces better code than gcc.

Hi,

what do you mean with better code? Is the code produced by open64 faster than the code produce by GCC? If yes, are you referring about the autoparallel capabilities? At the moment, Open64 has better autoparall framework than GCC. The next to releases of GCC 4.7 and 4.8 will have the new Graphite framework.
And finally, why open64 is not much used?

Thank

---

