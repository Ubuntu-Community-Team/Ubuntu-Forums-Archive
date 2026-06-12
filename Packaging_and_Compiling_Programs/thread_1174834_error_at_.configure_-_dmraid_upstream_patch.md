---
title: "error at ./configure - dmraid upstream patch"
date: 2009-05-31
forum: Packaging and Compiling Programs
---

### Post by Portending Ennui on 2009-05-31
Background:

I'm trying to get my FakeRaid controller to work (ICH-7M - Toshiba Raid Controller - Toshiba Qosmio G35 Notebook) and found a patch from a dev at redhat that is going into the next revision of dmraid.  From my digging, this probably wont hit ubuntu until karmic, so I was going to make a deb with the patch for 9.04 to last me if I need to reinstall.

I patched the file successfully, ran ./configure, and get the following output, stopping short of finishing.

```
 root@testbed:/usr/src/dmraid-1.0.0.rc15/1.0.0.rc15# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gawk... no
checking for mawk... mawk
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... yes
checking for ranlib... ranlib
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking for unistd.h... (cached) yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for off_t... yes
checking for pid_t... yes
checking for size_t... yes
checking for struct stat.st_rdev... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether to enable debugging... 
no
checking whether to enable malloc debugging... 
no
checking whether to disable native metadata logging... 
yes
checking whether to disable testing with mapped devices... 
no
checking whether gcc needs -traditional... no
checking return type of signal handlers... void
checking for vprintf... yes
checking for _doprnt... no
checking for mkdir... yes
checking for rmdir... yes
checking for uname... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
configure: creating ./config.status
config.status: creating include/Makefile
config.status: creating lib/Makefile
config.status: creating man/Makefile
config.status: creating tools/Makefile
config.status: creating tools/version.h
config.status: creating Makefile
config.status: creating make.tmpl
config.status: WARNING:  make.tmpl.in seems to ignore the --datarootdir setting
root@testbed:/usr/src/dmraid-1.0.0.rc15/1.0.0.rc15# 
 
```

Note the last line.  I can not find any information on this error anywhere. So I ask of you ubuntu gurus assistance. ;)

Anyone have an idea?

I have build-essentials, automake, checkinstall, dmraid build-dep, all the stuff I need (I think).

---

