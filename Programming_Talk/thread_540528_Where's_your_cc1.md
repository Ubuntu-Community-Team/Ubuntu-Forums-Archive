---
title: "Where's your cc1 ?"
date: 2007-09-01
forum: Programming Talk
---

### Post by Martin12 on 2007-09-01
I'm using a freshly installed 7.04 system,with gcc and cpp installed but I'm unable to compile a simple C-programm:

m12@ubuntu:~$ gcc -v test.c
Es werden eingebaute Spezifikationen verwendet.
Ziel: i486-linux-gnu
Konfiguriert mit: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread-Modell: posix
gcc-Version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
 cc1 -quiet -v test.c -quiet -dumpbase test.c -mtune=generic -auxbase test -version -fstack-protector -fstack-protector -o /tmp/ccZvzQL3.s
gcc: error trying to exec 'cc1': execvp: No such file or directory

Tha's true: I do not have "cc1" on my system and it is not part of the
cpp package:

$dpkg -L cpp-4.1
/.
/usr
/usr/share
/usr/share/doc
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/cpp-4.1.1.gz
/usr/bin
/usr/bin/cpp-4.1
/usr/lib
/usr/lib/gcc
/usr/lib/gcc/i486-linux-gnu
/usr/lib/gcc/i486-linux-gnu/4.1.2
/usr/share/doc/cpp-4.1
/usr/share/man/man1/i486-linux-gnu-cpp-4.1.1.gz
/usr/bin/i486-linux-gnu-cpp-4.1


The corresponding debian-package (cpp-4.1 from stable) comprises the file
/usr/lib/gcc/i486-linux-gnu/4.1.2/cc1


Does anyone have the "cc1" on ubuntu 7.04? If so, where did you get if from ?

Here's what I have:

ii  cpp                     4.1.2-1ubuntu1
ii  cpp-4.1               4.1.2-0ubuntu4
ii  gcc                     4.1.2-1ubuntu1                      
ii  gcc-4.1               4.1.2-0ubuntu4                   
ii  gcc-4.1-base      4.1.2-0ubuntu4


-Martin

---

### Post by aks44 on 2007-09-01
I probably got it through the build-essential metapackage.

---

### Post by PaulFr on 2007-09-01
```
apt-file search cc1 | grep 'cc1$'
``` gives ```
bcc: usr/lib/bcc/bcc-cc1
cpp-3.3: usr/lib/gcc-lib/i486-linux-gnu/3.3.6/cc1
cpp-3.4: usr/lib/gcc/i486-linux-gnu/3.4.6/cc1
cpp-4.1: usr/lib/gcc/i486-linux-gnu/4.1.2/cc1
gcc-2.95: usr/lib/gcc-lib/i486-linux-gnu/2.95.4/cc1
gcc-avr: usr/libexec/gcc/avr/4.1.0/cc1
gcc-h8300-hms: usr/lib/gcc/h8300-hitachi-coff/3.4.6/cc1
gcc-m68hc1x: usr/lib/gcc-lib/m68hc11/3.3.6-m68hc1x-20060122/cc1
gcc-snapshot: usr/lib/gcc-snapshot/libexec/gcc/i486-linux-gnu/4.3.0/cc1
gcc272: usr/lib/gcc-lib/i486-linux-gnu/2.7.2.3/cc1
ghdl: usr/lib/ghdl/libexec/gcc/i486-linux-gnu/4.1.1/cc1
...
```Since **gcc -v** gives me gcc version 4.1.2 on my machine, I guess it has to be the cpp-4.1 package.

The build-essential package contains the gcc package which contains the cpp package, so installing either build-essential or gcc will give you the cpp package as well. Hope this helps.

---

### Post by Martin12 on 2007-09-02
> **PaulFr said:**
> ```
apt-file search cc1 | grep 'cc1$'
``` gives ```
...
cpp-4.1: usr/lib/gcc/i486-linux-gnu/4.1.2/cc1
...
...
```Since **gcc -v** gives me gcc version 4.1.2 on my machine, I guess it has to be the cpp-4.1 package.

The build-essential package contains the gcc package which contains the cpp package, so installing either build-essential or gcc will give you the cpp package as well. Hope this helps.

Which cpp-4.12 version are you using? I have gcc (and cpp) installed
but cannot find a trace of cc1 on my system.
```


root@ubuntu:~# dpkg -s cpp-4.1
Package: cpp-4.1
Status: install ok installed
Priority: optional
Section: interpreters
Installed-Size: 5208
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: gcc-4.1
Version: 4.1.2-0ubuntu4
Replaces: gcj-4.1 (<< 4.1.1)
Depends: gcc-4.1-base (= 4.1.2-0ubuntu4), libc6 (>= 2.5-0ubuntu1)
Suggests: gcc-4.1-locales (>= 4.1.2)
Conflicts: gcj-4.1 (<< 4.1.1)
Description: The GNU C preprocessor
 A macro processor that is used automatically by the GNU C compiler
 to transform programs before actual compilation.
 .
 This package has been separated from gcc for the benefit of those who
 require the preprocessor but not the compiler.
Original-Maintainer: Debian GCC Maintainers <debian-gcc@lists.debian.org>

```

This package does not contain cc1 as verified by dpkg:
```

root@ubuntu:~# dpkg -L cpp-4.1
/.
/usr
/usr/share
/usr/share/doc
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/cpp-4.1.1.gz
/usr/bin
/usr/bin/cpp-4.1
/usr/lib
/usr/lib/gcc
/usr/lib/gcc/i486-linux-gnu
/usr/lib/gcc/i486-linux-gnu/4.1.2
/usr/share/doc/cpp-4.1
/usr/share/man/man1/i486-linux-gnu-cpp-4.1.1.gz
/usr/bin/i486-linux-gnu-cpp-4.1

```

In my opinion, cc1 SHOULD be installed by cpp-4.1 (like it is on your system) , but it does not seem to be part of  the 4.1.2-0ubuntu4 package.

---

### Post by talowe on 2007-09-03
> **Martin12 said:**
> 

In my opinion, cc1 SHOULD be installed by cpp-4.1 (like it is on your system) , but it does not seem to be part of  the 4.1.2-0ubuntu4 package.

```
tom@ourhome:~$ dpkg -s cpp-4.1
Package: cpp-4.1
Status: install ok installed
Priority: optional
Section: interpreters
Installed-Size: 5208
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: gcc-4.1
Version: 4.1.2-0ubuntu4
Replaces: gcj-4.1 (<< 4.1.1)
Depends: gcc-4.1-base (= 4.1.2-0ubuntu4), libc6 (>= 2.5-0ubuntu1)
Suggests: gcc-4.1-locales (>= 4.1.2)
Conflicts: gcj-4.1 (<< 4.1.1)
Description: The GNU C preprocessor
 A macro processor that is used automatically by the GNU C compiler
 to transform programs before actual compilation.
 .
 This package has been separated from gcc for the benefit of those who
 require the preprocessor but not the compiler.
Original-Maintainer: Debian GCC Maintainers <debian-gcc@lists.debian.org>
tom@ourhome:~$ dpkg -L cpp-4.1
/.
/usr
/usr/share
/usr/share/doc
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/cpp-4.1.1.gz
/usr/bin
/usr/bin/cpp-4.1
/usr/lib
/usr/lib/gcc
/usr/lib/gcc/i486-linux-gnu
/usr/lib/gcc/i486-linux-gnu/4.1.2
/usr/lib/gcc/i486-linux-gnu/4.1.2/cc1
/usr/share/doc/cpp-4.1
/usr/share/man/man1/i486-linux-gnu-cpp-4.1.1.gz
/usr/bin/i486-linux-gnu-cpp-4.1



```

Maybe you should try re-install of cpp-4.1?

---

### Post by Martin12 on 2007-09-07
solved by forcing a re-install of the cpp packe.
I still don't know why cc1 got removed from my package database (dpkg did not list it)

---

### Post by jaloo on 2011-03-01
gcc -print-prog-name=cc1

---

### Post by lisati on 2011-03-01
May the thread rest in peace.

---

