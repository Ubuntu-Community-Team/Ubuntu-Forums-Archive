---
title: "Can't Compile Package"
date: 2007-09-14
forum: Packaging and Compiling Programs
---

### Post by init1 on 2007-09-14
This package will not compile. I ran:
```

./configure
make
make install

```
And I got lots of errors
I have the build essentials and gcc. Any ideas?
[http://karmen.sourceforge.net/](http://karmen.sourceforge.net/)

---

### Post by lisati on 2007-09-14
Are you able to copy some of the errors? (the first few are most likely to be of help.....)

---

### Post by init1 on 2007-09-14
It worked when I compiled it in Vector. Weird. 
Here what I get in Debian:
```

./configure

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
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
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for X... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: executing depfiles commands

The error list is so long, I cannot copy/paste it. How do I post it then? make>error does not work.

---

