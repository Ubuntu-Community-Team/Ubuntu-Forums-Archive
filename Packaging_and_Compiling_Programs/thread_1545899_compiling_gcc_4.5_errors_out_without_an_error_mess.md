---
title: "compiling gcc 4.5 errors out without an error message"
date: 2010-08-04
forum: Packaging and Compiling Programs
---

### Post by zeddicus76 on 2010-08-04
I am trying to compile gcc 4.5 on Ubuntu 10.4 x86_64. The commands I used to configured and compile are:

```

svn co svn://gcc.gnu.org/svn/gcc/tags/gcc_4_5_0_release .
../configure --prefix=/usr/local/gcc45 --disable-multilib
make
```

The compilation ends as follows. Also I have tried the same thing on an openSUSE 11.3 machine and got the same exact ending.

```
rm -rf asm classes classes.lst asm.lst
make  all-am
make[5]: Entering directory `/home/gavin/src/gcc/4.5.0/gcc-build/x86_64-unknown-linux-gnu/libjava/classpath/tools'
Makefile:857: warning: overriding commands for target `gjdoc'
Makefile:775: warning: ignoring old commands for target `gjdoc'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/gavin/src/gcc/4.5.0/gcc-build/x86_64-unknown-linux-gnu/libjava/classpath/tools'
make[4]: Leaving directory `/home/gavin/src/gcc/4.5.0/gcc-build/x86_64-unknown-linux-gnu/libjava/classpath/tools'
make[4]: Entering directory `/home/gavin/src/gcc/4.5.0/gcc-build/x86_64-unknown-linux-gnu/libjava/classpath'
true  DO=all multi-do # make
make[4]: Leaving directory `/home/gavin/src/gcc/4.5.0/gcc-build/x86_64-unknown-linux-gnu/libjava/classpath'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/gavin/src/gcc/4.5.0/gcc-build/x86_64-unknown-linux-gnu/libjava/classpath'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/gavin/src/gcc/4.5.0/gcc-build/x86_64-unknown-linux-gnu/libjava'
make[1]: *** [all-target-libjava] Error 2
make[1]: Leaving directory `/home/gavin/src/gcc/4.5.0/gcc-build'
```

Any help to get this to complete would be very welcome.
Thank you,
Gavin

---

