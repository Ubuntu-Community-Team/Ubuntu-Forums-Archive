---
title: "Can't seem to automake"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by wc5b on 2013-03-01
I am starting to think I can't seem to automake ANYTHING. I have another post of something similar happening with device drivers, but this seems to be doing something similar and is just a simple application. (Sort of a database log)

The install readme simply states it supports automake and should have to just ./configure, make, install make. But this is what I get when I try. Very similar to my other post with the drivers:

```
wc5b@wc5b-mint ~/Downloads/tlf/tlf-0.9.30 $ lsacconfig.h    ChangeLog     config.log     configure.in  INSTALL      Makefile.in    README   src
acinclude.m4  config.guess  config.status  COPYING       install-sh   missing        rules    stamp-h1
aclocal.m4    config.h      config.sub     depcomp       Makefile     mkinstalldirs  scripts  tlf.1
AUTHORS       config.h.in   configure      doc           Makefile.am  NEWS           share    tlf.1.in
wc5b@wc5b-mint ~/Downloads/tlf/tlf-0.9.30 $ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... (cached) gawk
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking for unistd.h... (cached) yes
checking for atan in -lm... yes
checking for pthread_create in -lpthread... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for the pthreads library -lpthreads... no
checking whether pthreads work without any flags... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... no
checking for cc_r... gcc
checking for initscr in -lncurses... no
disabling hamlib support
checking for pid_t... yes
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking whether gcc needs -traditional... no
checking for strftime... yes
checking for floor... yes
checking for sqrt... yes
checking for strchr... yes
checking for strcspn... yes
checking for strspn... yes
checking for strstr... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating doc/Makefile
config.status: creating rules/Makefile
config.status: creating scripts/Makefile
config.status: creating share/Makefile
config.status: creating src/Makefile
config.status: creating tlf.1
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
wc5b@wc5b-mint ~/Downloads/tlf/tlf-0.9.30 $ make
make  all-recursive
make[1]: Entering directory `/home/wc5b/Downloads/tlf/tlf-0.9.30'
Making all in doc
make[2]: Entering directory `/home/wc5b/Downloads/tlf/tlf-0.9.30/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/wc5b/Downloads/tlf/tlf-0.9.30/doc'
Making all in rules
make[2]: Entering directory `/home/wc5b/Downloads/tlf/tlf-0.9.30/rules'
make[3]: Entering directory `/home/wc5b/Downloads/tlf/tlf-0.9.30/rules'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/wc5b/Downloads/tlf/tlf-0.9.30/rules'
make[2]: Leaving directory `/home/wc5b/Downloads/tlf/tlf-0.9.30/rules'
Making all in src
make[2]: Entering directory `/home/wc5b/Downloads/tlf/tlf-0.9.30/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -Wall -MT addarea.o -MD -MP -MF ".deps/addarea.Tpo" -c -o addarea.o addarea.c; \
	then mv -f ".deps/addarea.Tpo" ".deps/addarea.Po"; else rm -f ".deps/addarea.Tpo"; exit 1; fi
In file included from globalvars.h:1:0,
                 from addarea.c:25:
tlf.h:23:20: fatal error: curses.h: No such file or directory
compilation terminated.
make[2]: *** [addarea.o] Error 1
make[2]: Leaving directory `/home/wc5b/Downloads/tlf/tlf-0.9.30/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/wc5b/Downloads/tlf/tlf-0.9.30'
make: *** [all] Error 2
wc5b@wc5b-mint ~/Downloads/tlf/tlf-0.9.30 $ make install
Making install in doc
make[1]: Entering directory `/home/wc5b/Downloads/tlf/tlf-0.9.30/doc'
make[2]: Entering directory `/home/wc5b/Downloads/tlf/tlf-0.9.30/doc'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash ../mkinstalldirs /usr/local/share/tlf/doc
mkdir /usr/local/share/tlf
mkdir: cannot create directory `/usr/local/share/tlf': Permission denied
mkdir /usr/local/share/tlf/doc
mkdir: cannot create directory `/usr/local/share/tlf/doc': No such file or directory
make[2]: *** [install-data-local] Error 1
make[2]: Leaving directory `/home/wc5b/Downloads/tlf/tlf-0.9.30/doc'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/wc5b/Downloads/tlf/tlf-0.9.30/doc'
make: *** [install-recursive] Error 1
wc5b@wc5b-mint ~/Downloads/tlf/tlf-0.9.30 $ 



```

Any help is welcomed. Thanks.

---

### Post by iponeverything on 2013-03-01
I see two things -- 

install curses dev and do the make install as root.

---

