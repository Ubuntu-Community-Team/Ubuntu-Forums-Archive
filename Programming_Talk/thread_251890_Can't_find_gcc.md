---
title: "Can't find gcc"
date: 2006-09-06
forum: Programming Talk
---

### Post by MdaG on 2006-09-06
I need to build Vim7. Since I can't find it using apt I guess I'll have to build it from source. But when I try it says that gcc is an unknown command. Where do I find gcc (I guess it's somewhere on my drive) and how do I add it to my $PATH ?
```
./configure
configure: loading cache auto/config.cache
checking whether make sets $(MAKE)... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
```

---

### Post by toojays on 2006-09-06
You need to install the build-essential package.

---

### Post by raldz on 2006-09-06
Search/Install "kernel-source" "gcc-c++" " and "make" using Synaptics..

---

### Post by MdaG on 2006-09-06
> **toojays said:**
> You need to install the build-essential package.
These? (As far as I can tell gcc is already installed, but as version 3.4)
```
$ sudo apt-get -s install gcc
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils cpp cpp-4.0 gcc-4.0
Suggested packages:
  binutils-doc cpp-doc gcc-4.0-locales make manpages-dev autoconf automake1.9
  libtool flex bison gcc-doc gcc-4.0-doc libc6-dev-amd64 lib64gcc1
Recommended packages:
  libc6-dev libc-dev libmudflap0-dev
The following NEW packages will be installed:
  binutils cpp cpp-4.0 gcc gcc-4.0
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Inst binutils (2.16.1cvs20060117-1ubuntu2.1 Ubuntu:6.06/dapper-security)
Inst cpp-4.0 (4.0.3-1ubuntu5 Ubuntu:6.06/dapper)
Inst cpp (4:4.0.3-1 Ubuntu:6.06/dapper)
Inst gcc-4.0 (4.0.3-1ubuntu5 Ubuntu:6.06/dapper)
Inst gcc (4:4.0.3-1 Ubuntu:6.06/dapper)
Conf binutils (2.16.1cvs20060117-1ubuntu2.1 Ubuntu:6.06/dapper-security)
Conf cpp-4.0 (4.0.3-1ubuntu5 Ubuntu:6.06/dapper)
Conf cpp (4:4.0.3-1 Ubuntu:6.06/dapper)
Conf gcc-4.0 (4.0.3-1ubuntu5 Ubuntu:6.06/dapper)
Conf gcc (4:4.0.3-1 Ubuntu:6.06/dapper)
```
Can't find gcc-c++, but this gives me:
```
$ sudo apt-get -s install gcc kernel-source make
Reading package lists... Done
Building dependency tree... Done
Note, selecting kernel-source-2.4.27 instead of kernel-source
The following extra packages will be installed:
  binutils cpp cpp-4.0 gcc-4.0 kernel-source-2.4.27
Suggested packages:
  binutils-doc cpp-doc gcc-4.0-locales manpages-dev autoconf automake1.9
  libtool flex bison gcc-doc gcc-4.0-doc libc6-dev-amd64 lib64gcc1
  libncurses5-dev libncurses-dev tk8.4-dev tk-dev kernel-package
Recommended packages:
  libc6-dev libc-dev libmudflap0-dev gcc-3.3
The following NEW packages will be installed:
  binutils cpp cpp-4.0 gcc gcc-4.0 kernel-source-2.4.27 make
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Inst binutils (2.16.1cvs20060117-1ubuntu2.1 Ubuntu:6.06/dapper-security)
Inst cpp-4.0 (4.0.3-1ubuntu5 Ubuntu:6.06/dapper)
Inst cpp (4:4.0.3-1 Ubuntu:6.06/dapper)
Inst gcc-4.0 (4.0.3-1ubuntu5 Ubuntu:6.06/dapper)
Inst gcc (4:4.0.3-1 Ubuntu:6.06/dapper)
Inst kernel-source-2.4.27 (2.4.27-12 Ubuntu:6.06/dapper)
Inst make (3.80+3.81.b4-1 Ubuntu:6.06/dapper)
Conf binutils (2.16.1cvs20060117-1ubuntu2.1 Ubuntu:6.06/dapper-security)
Conf cpp-4.0 (4.0.3-1ubuntu5 Ubuntu:6.06/dapper)
Conf cpp (4:4.0.3-1 Ubuntu:6.06/dapper)
Conf gcc-4.0 (4.0.3-1ubuntu5 Ubuntu:6.06/dapper)
Conf gcc (4:4.0.3-1 Ubuntu:6.06/dapper)
Conf kernel-source-2.4.27 (2.4.27-12 Ubuntu:6.06/dapper)
Conf make (3.80+3.81.b4-1 Ubuntu:6.06/dapper)
magnus@magnus-laptop:~/software/vim70$
```

---

### Post by toojays on 2006-09-06
No, there is literally a package called "build-essential". Install that.

---

### Post by MdaG on 2006-09-06
> **toojays said:**
> No, there is literally a package called "build-essential". Install that.
Aah, I understand. :-)
Now it's complaining about ncurses which according to Synaptic is already installed...
```
.
.
.
checking --with-tlib argument... empty: automatic terminal library selection
checking for tgetent in -lncurses... no
checking for tgetent in -ltermlib... no
checking for tgetent in -ltermcap... no
checking for tgetent in -lcurses... no
no terminal library found
checking for tgetent()... configure: error: NOT FOUND!
      You need to install a terminal library; for example ncurses.
      Or specify the name of the library with --with-tlib.
```
Using: ./configure --with-tlib=libncurses5
doesn't help either... :confused:

---

### Post by toojays on 2006-09-06
When you get configure scripts complaining about missing libraries, it usually means you need to install the -dev package for that library. So for the package libncurses5, you need to install libncurses5-dev.

---

### Post by bosshoff on 2006-11-30
Thank you for your reply to this thread, toojays.  I was having similar trouble with a ./configure script requiring ncurses, and your succinct reply made all the difference.

---

