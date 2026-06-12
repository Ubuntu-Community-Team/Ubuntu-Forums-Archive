---
title: "Automake error"
date: 2009-09-20
forum: Programming Talk
---

### Post by matmatmat on 2009-09-20
I am following [this]("http://www.openismus.com/documents/linux/automake/automake.shtml") tutorial, my configure.ac is:
```

AC_INIT(main.cc)

AM_INIT_AUTOMAKE(hello,0.1)

AC_CONFIG_HEADERS(helloworld.h)

AC_PROG_CC

AC_PROG_CXX

AC_PROG_INSTALL

AC_OUTPUT(Makefile)

bin_PROGRAMS = hello
hello_SOURCES = helloworld.h helloworld.cc main.cc

```
when run:
```

matio@matio-desktop:~/Documents/C++/gtk/helloworld$ aclocal
matio@matio-desktop:~/Documents/C++/gtk/helloworld$ autoconf 
matio@matio-desktop:~/Documents/C++/gtk/helloworld$ automake
matio@matio-desktop:~/Documents/C++/gtk/helloworld$ ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... none
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... none
checking for a BSD-compatible install... /usr/bin/install -c
configure: creating ./config.status
config.status: creating Makefile
config.status: creating helloworld.h
config.status: helloworld.h is unchanged
config.status: executing depfiles commands
./configure: line 5415: bin_PROGRAMS: command not found
./configure: line 5416: hello_SOURCES: command not found

```
what's wrong?

---

### Post by januzi on 2009-09-20
Put:
> 
bin_PROGRAMS = hello
hello_SOURCES = helloworld.h helloworld.cc main.ccinto the Makefile.am

---

### Post by matmatmat on 2009-09-21
It still doesn't work

---

### Post by januzi on 2009-09-21
What's the error ? Did You remember to remove those two lines from configure.ac ?

---

