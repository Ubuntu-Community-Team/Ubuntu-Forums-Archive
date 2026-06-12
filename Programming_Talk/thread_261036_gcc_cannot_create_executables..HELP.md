---
title: "gcc cannot create executables..HELP"
date: 2006-09-19
forum: Programming Talk
---

### Post by Nectron on 2006-09-19
I have installed gcc 4.0.3 on my ubuntu 6.06 LTS.. When I tried to ```
./configure
``` kismet (and other programs too), I got the error (gcc cannot create executables, see config.log)..

Here's the config.log for kismet:
```

## ----------- ##
## Core tests. ##
## ----------- ##

configure:1367: checking build system type
configure:1385: result: i686-pc-linux-gnulibc1
configure:1393: checking host system type
configure:1407: result: i686-pc-linux-gnulibc1
configure:1463: checking for gcc
configure:1479: found /usr/bin/gcc
configure:1489: result: gcc
configure:1733: checking for C compiler version
configure:1736: gcc --version </dev/null >&5
gcc (GCC) 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:1739: $? = 0
configure:1741: gcc -v </dev/null >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.0 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-awt=gtk-default --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --with-tune=pentium4 --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
configure:1744: $? = 0
configure:1746: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:1749: $? = 1
configure:1772: checking for C compiler default output file name
configure:1775: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:1778: $? = 1
configure: failed program was:
| /* confdefs.h.  */

```

What should I do to fix this problem? Have I done anything wrong during installation ?

Thanks in advance ;)

---

### Post by thumper on 2006-09-20
did you install gcc or build-essential?

---

### Post by Nectron on 2006-09-20
I got it through the Synaptic Package Manager using the Ubuntu DVD..

---

### Post by thumper on 2006-09-20
but did you just select the package gcc?

If you did, go back and select the package "build-essential"

---

### Post by Nectron on 2006-09-20
I've just installed build-essentials and tried to run ./configure again..

it couldn't detect "libncurses", so I installed that too..

Now everything is going fine..

What packages do I need to compile a program? I might need them in the future for reference..

Thanks all..

---

### Post by thumper on 2006-09-20
You need build-essential plus all the other libraries that your program links against, such as libncurses.

---

### Post by pclapham on 2006-09-21
Thanks to all of you.  This thread answered my questions, too.  One wonders -- could Ubuntu list "build-essentials" as a dependency for "gcc"?

---

