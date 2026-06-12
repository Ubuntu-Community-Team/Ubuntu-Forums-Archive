---
title: "error while compiling packages"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by lio_013 on 2008-08-23
many times i try to install packages with extension (tar.bz2)
and i always fail
the ./configure instruction is ok
but when i type make 
it gives me an error message 
```
*** No targets specified and no makefile found.  Stop.
```
any one can help 
thanks
:confused::confused::confused:

edit by OldSoldier: please refrain from using the large fonts

---

### Post by lio_013 on 2008-08-23
```

ahmed@Lio:~/Desktop/knetworkmanager-0.1$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... no
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... no
checking whether g++ supports -Wno-long-long... no
checking whether g++ supports -Wno-non-virtual-dtor... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
ahmed@Lio:~/Desktop/knetworkmanager-0.1$ make
make: *** No targets specified and no makefile found.  Stop.
ahmed@Lio:~/Desktop/knetworkmanager-0.1$ makefile
bash: makefile: command not found
ahmed@Lio:~/Desktop/knetworkmanager-0.1$ make
make: *** No targets specified and no makefile found.  Stop.
ahmed@Lio:~/Desktop/knetworkmanager-0.1$ CC=c89 CFLAGS=-O2 LIBS=-lposix ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... c89
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
ahmed@Lio:~/Desktop/knetworkmanager-0.1$ make
make: *** No targets specified and no makefile found.  Stop.

```

[COLOR="Blue"][SIZE="5"]that was a copy of my terminal i wish it will help[/SIZE][/COLOR]

---

### Post by oldos2er on 2008-08-23
You need to install the package "build-essential".

---

### Post by Oldsoldier2003 on 2008-08-23
> **oldos2er said:**
> You need to install the package "build-essential".

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
```
but on a semi-related subject, are you positive you need to compile the package? Try the repositories first. There are not many packages that a new user would need to compile right away.

---

