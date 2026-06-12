---
title: "compiling  OpenMP"
date: 2011-02-22
forum: Programming Talk
---

### Post by biebo on 2011-02-22
hello all,

my gcc doesn't compile openmp programs.

gcc -fopenmp hellomp.c
[COLOR=Red]hellomp.c:2:17: error: omp.h: No such file or directory[/COLOR]


gcc -v 

Using built-in specs.
Target: i686-pc-linux-gnu
Configured with: /home/build/svn/trunk/eng/prod/gcc/configure --prefix=/home/build/32/local/cilk --with-gas-weakref=no --with-comdat-group --enable-checking --disable-bootstrap --disable-libgomp --enable-languages=c,c++ --disable-libstdcxx-pch --enable-targets=all --with-cilk-version=10100 --with-cilk-build=8503
Thread model: posix
gcc version 4.2.4 (Cilk Arts build 8503)


Thanks

---

### Post by biebo on 2011-02-22
hello all,

my gcc doesn't compile openmp programs.

gcc -fopenmp hellomp.c
[COLOR=Red]hellomp.c:2:17: error: omp.h: No such file or directory[/COLOR]


gcc -v 

Using built-in specs.
Target: i686-pc-linux-gnu
Configured with: /home/build/svn/trunk/eng/prod/gcc/configure --prefix=/home/build/32/local/cilk --with-gas-weakref=no --with-comdat-group --enable-checking --disable-bootstrap --disable-libgomp --enable-languages=c,c++ --disable-libstdcxx-pch --enable-targets=all --with-cilk-version=10100 --with-cilk-build=8503
Thread model: posix
gcc version 4.2.4 (Cilk Arts build 8503)


Thanks

---

### Post by lykeion on 2011-02-22
Did you include omp.h? What's your code?
See this: [http://wiki.bath.ac.uk/display/HPC/OpenMP](http://wiki.bath.ac.uk/display/HPC/OpenMP)

---

### Post by cjcopi on 2011-02-22
You have configured gcc without openmp support.  The --disable-libgomp configure option is what does this.  You must either reconfigure and recompile your version of gcc without this option or use a version of gcc that supports openmp, such as the one that comes with your version of ubuntu.

---

### Post by talonmies on 2011-02-22
The compiler you are trying to use is the now decprecated Cilk Arts Cilk++ compiler. It supports compiler assisted parallelism, but not OpenMP.

---

### Post by MadCow108 on 2011-02-22
don't open multiple threads on the same issue ...
[http://ubuntuforums.org/showthread.php?t=1693003](http://ubuntuforums.org/showthread.php?t=1693003)

edit: obsolete, merged by the helpful moderators (wow < 1 min reaction time)

---

### Post by howefield on 2011-02-22
Threads merged.

---

