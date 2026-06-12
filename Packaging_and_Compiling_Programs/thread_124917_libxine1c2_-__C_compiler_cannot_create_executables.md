---
title: "libxine1c2 -  C compiler cannot create executables"
date: 2006-02-02
forum: Packaging and Compiling Programs
---

### Post by jgoshorn on 2006-02-02
Thanks for reading this. . .

I'm trying to compile libxine1c2 and get the following error:
configure: error: C compiler cannot create executables

The config.log reads in part:

configure:2523: $? = 0
configure:2525: gcc -v </dev/null >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --with-gxx-include-dir=/usr/include/c++/4.0.2 --enable-shared --with-system-zlib --libexecdir=/usr/lib --enable-nls --without-included-gettext --enable-threads=posix --program-suffix=-4.0 --enable-__cxa_atexit --enable-libstdcxx-allocator=mt --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-gc=boehm --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
configure:2528: $? = 0
configure:2530: gcc -V </dev/null >&5
gcc: couldn't run 'i486-linux-gnu-gcc--O3': Invalid argument
configure:2533: $? = 1
configure:2557: checking for C compiler default output
configure:2560: gcc -g   conftest.c  >&5
`-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.
collect2: cannot find 'ld'
configure:2563: $? = 1
configure: failed program was:
| #line 2536 "configure"
| /* confdefs.h.  */

I welcome suggestions as to how to fix this.  Thanks in advance.

---

### Post by gord on 2006-02-03
```
sudo apt-get install build-essential
```
might help

---

### Post by jgoshorn on 2006-02-03
It's already installed.

---

### Post by joegoggins on 2006-04-11
yep. this worked for me.
thanks

---

### Post by mistabob on 2006-04-20
i have the same problem and can't figure out what's wrong, i pdkg-reconfigured anything i could and still have the same problem, i have the same problem with anything i try to dpk-build. make, and so ld, works for programs i compile from the tar.gz it must be some dpkg-build bug
i added the backports to my sources.list maybe it's the source of the problem 
help please !!!

---

### Post by eyes_on_the_net on 2006-05-08
I had the same problem after just installing make and gcc. Ran the code suggested by gord and I could compile.  I was trying to compile the meanwhile plugin for gaim so I can use my Linux desktop to connect to the Lotus Sametime servers.

---

### Post by Skukfas on 2006-09-14
same problem here, and it helped...
thx

---

### Post by insidex on 2007-06-07
Thx, it's help me too :KS

---

### Post by saurabh321 on 2007-07-15
Hi all,
I am running Ubuntu 6.06 LTS from my PenDrive on Compaq presario v6211au notebook.
I was unable to compile reSIProcate as it said "C compiler can not create executables".
doing 
<code> 
sudo apt-get install build-essential
</code>

solved my problem.

Thnaks Ubuntu Community.

---

### Post by Slyker on 2008-01-04
Thank you, this worked for me.  It was my first attempt at a build and I could not have done it without your help.

---

### Post by Dafidov on 2008-10-21
Hello.
This solution helped me too.
Best regards

---

