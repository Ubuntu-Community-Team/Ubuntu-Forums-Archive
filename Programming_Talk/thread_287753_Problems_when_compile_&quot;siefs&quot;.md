---
title: "Problems when compile &quot;siefs&quot;"
date: 2006-10-29
forum: Programming Talk
---

### Post by emil.s on 2006-10-29
```
emil@Sandnabba: ~/Desktop/siefs-0.5 $ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/emil/Desktop/siefs-0.5/missing: Unknown `--run' option
Try `/home/emil/Desktop/siefs-0.5/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for ranlib... ranlib
checking fuse installation... /usr/local
configure: creating ./config.status
config.status: creating Makefile
config.status: creating siefs/Makefile
config.status: creating converter/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
emil@Sandnabba: ~/Desktop/siefs-0.5 $ make
make  all-recursive
make[1]: Entering directory `/home/emil/Desktop/siefs-0.5'
Making all in siefs
make[2]: Entering directory `/home/emil/Desktop/siefs-0.5/siefs'
gcc  -I/usr/local/include -DFUSEINST="\"/usr/local\"" -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=22  -L/lib -o siefs  siefs.o obex.o transport.o comm.o crcmodel.o charset.o /usr/local/lib/libfuse.a -lpthread
/usr/local/lib/libfuse.a(fuse.o): In function `curr_time':
/home/emil/Desktop/fuse-2.6.0/lib/fuse.c:738: undefined reference to `clock_gettime'
/home/emil/Desktop/fuse-2.6.0/lib/fuse.c:741: undefined reference to `clock_gettime'
collect2: ld returned 1 exit status
make[2]: *** [siefs] Error 1
make[2]: Leaving directory `/home/emil/Desktop/siefs-0.5/siefs'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/emil/Desktop/siefs-0.5'
make: *** [all] Error 2
```
Any experienced programmer who see what's wrong? :p

---

### Post by po0f on 2006-10-29
emil.s,

The program is not linking with the rt library.  Look in Makefile for a variable called LIBS or LIBRARIES and post back what it says.

If you can find where in the Makefile it has -lpthread, just add -lrt to it as well.

---

### Post by emil.s on 2006-10-29
> **po0f said:**
> emil.s,

The program is not linking with the rt library.  Look in Makefile for a variable called LIBS or LIBRARIES and post back what it says.

If you can find where in the Makefile it has -lpthread, just add -lrt to it as well.

Hm,
```
emil@Sandnabba: ~/Desktop/siefs-0.5 $ cat Makefile* | grep lpthread
emil@Sandnabba: ~/Desktop/siefs-0.5 $

```
:???:

---

### Post by po0f on 2006-10-29
emil.s,

You might have to recompile the fuse library.  It looks like it's actually that library that you compiled that's complaining.

---

### Post by emil.s on 2006-10-30
> **po0f said:**
> emil.s,

You might have to recompile the fuse library.  It looks like it's actually that library that you compiled that's complaining.

```

emil@Sandnabba: ~/Desktop/fuse-2.6.0 $ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 32768
checking whether the shell understands some XSI constructs... yes
checking for /usr/bin/ld option to reload object files... -r
checking how to recognise dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for fork... yes
checking for setxattr... yes
checking for fdatasync... yes
checking for struct stat.st_atim... yes
checking for struct stat.st_atimespec... no
checking for library containing clock_gettime... -lrt
checking selinux/selinux.h usability... no
checking selinux/selinux.h presence... no
checking for selinux/selinux.h... no
configure: creating ./config.status
config.status: creating fuse.pc
config.status: creating Makefile
config.status: creating lib/Makefile
config.status: creating util/Makefile
config.status: creating example/Makefile
config.status: creating include/Makefile
config.status: creating include/config.h
config.status: executing depfiles commands
config.status: executing libtool commands
=== configuring in kernel (/home/emil/Desktop/fuse-2.6.0/kernel)
configure: running /bin/bash ./configure --prefix=/usr/local  --cache-file=/dev/null --srcdir=.
checking for a BSD-compatible install... /usr/bin/install -c
checking if FUSE is loaded as a module... yes
checking if FUSE module is from official kernel... yes
configure:
NOTE:     Detected that FUSE is already present in the kernel, so
NOTE:     building of kernel module is disabled.  To force building
NOTE:     of kernel module use the '--enable-kernel-module' option.
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
emil@Sandnabba: ~/Desktop/fuse-2.6.0 $ make
Making all in kernel
make[1]: Entering directory `/home/emil/Desktop/fuse-2.6.0/kernel'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/emil/Desktop/fuse-2.6.0/kernel'
Making all in include
make[1]: Entering directory `/home/emil/Desktop/fuse-2.6.0/include'
make  all-am
make[2]: Entering directory `/home/emil/Desktop/fuse-2.6.0/include'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/emil/Desktop/fuse-2.6.0/include'
make[1]: Leaving directory `/home/emil/Desktop/fuse-2.6.0/include'
Making all in lib
make[1]: Entering directory `/home/emil/Desktop/fuse-2.6.0/lib'
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include  -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26   -Wall -W -g -O2 -MT fuse.lo -MD -MP -MF ".deps/fuse.Tpo" -c -o fuse.lo fuse.c; \
        then mv -f ".deps/fuse.Tpo" ".deps/fuse.Plo"; else rm -f ".deps/fuse.Tpo"; exit 1; fi
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT fuse.lo -MD -MP -MF .deps/fuse.Tpo -c fuse.c  -fPIC -DPIC -o .libs/fuse.o
fuse.c: In function 'fuse_compat_open':
fuse.c:2848: warning: dereferencing type-punned pointer will break strict-aliasing rules
fuse.c:2855: warning: dereferencing type-punned pointer will break strict-aliasing rules
fuse.c: In function 'fuse_compat_release':
fuse.c:2869: warning: dereferencing type-punned pointer will break strict-aliasing rules
fuse.c: In function 'fuse_compat_opendir':
fuse.c:2885: warning: dereferencing type-punned pointer will break strict-aliasing rules
fuse.c: In function 'fuse_compat_statfs':
fuse.c:2927: warning: dereferencing type-punned pointer will break strict-aliasing rules
fuse.c:2935: warning: dereferencing type-punned pointer will break strict-aliasing rules
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT fuse.lo -MD -MP -MF .deps/fuse.Tpo -c fuse.c -o fuse.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include  -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26   -Wall -W -g -O2 -MT fuse_kern_chan.lo -MD -MP -MF ".deps/fuse_kern_chan.Tpo" -c -o fuse_kern_chan.lo fuse_kern_chan.c; \
        then mv -f ".deps/fuse_kern_chan.Tpo" ".deps/fuse_kern_chan.Plo"; else rm -f ".deps/fuse_kern_chan.Tpo"; exit 1; fi
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT fuse_kern_chan.lo -MD -MP -MF .deps/fuse_kern_chan.Tpo -c fuse_kern_chan.c  -fPIC -DPIC -o .libs/fuse_kern_chan.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT fuse_kern_chan.lo -MD -MP -MF .deps/fuse_kern_chan.Tpo -c fuse_kern_chan.c -o fuse_kern_chan.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include  -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26   -Wall -W -g -O2 -MT fuse_loop.lo -MD -MP -MF ".deps/fuse_loop.Tpo" -c -o fuse_loop.lo fuse_loop.c; \
        then mv -f ".deps/fuse_loop.Tpo" ".deps/fuse_loop.Plo"; else rm -f ".deps/fuse_loop.Tpo"; exit 1; fi
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT fuse_loop.lo -MD -MP -MF .deps/fuse_loop.Tpo -c fuse_loop.c  -fPIC -DPIC -o .libs/fuse_loop.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT fuse_loop.lo -MD -MP -MF .deps/fuse_loop.Tpo -c fuse_loop.c -o fuse_loop.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include  -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26   -Wall -W -g -O2 -MT fuse_loop_mt.lo -MD -MP -MF ".deps/fuse_loop_mt.Tpo" -c -o fuse_loop_mt.lo fuse_loop_mt.c; \
        then mv -f ".deps/fuse_loop_mt.Tpo" ".deps/fuse_loop_mt.Plo"; else rm -f ".deps/fuse_loop_mt.Tpo"; exit 1; fi
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT fuse_loop_mt.lo -MD -MP -MF .deps/fuse_loop_mt.Tpo -c fuse_loop_mt.c  -fPIC -DPIC -o .libs/fuse_loop_mt.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT fuse_loop_mt.lo -MD -MP -MF .deps/fuse_loop_mt.Tpo -c fuse_loop_mt.c -o fuse_loop_mt.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include  -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26   -Wall -W -g -O2 -MT fuse_lowlevel.lo -MD -MP -MF ".deps/fuse_lowlevel.Tpo" -c -o fuse_lowlevel.lo fuse_lowlevel.c; \
        then mv -f ".deps/fuse_lowlevel.Tpo" ".deps/fuse_lowlevel.Plo"; else rm -f ".deps/fuse_lowlevel.Tpo"; exit 1; fi
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT fuse_lowlevel.lo -MD -MP -MF .deps/fuse_lowlevel.Tpo -c fuse_lowlevel.c  -fPIC -DPIC -o .libs/fuse_lowlevel.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT fuse_lowlevel.lo -MD -MP -MF .deps/fuse_lowlevel.Tpo -c fuse_lowlevel.c -o fuse_lowlevel.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include  -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26   -Wall -W -g -O2 -MT fuse_mt.lo -MD -MP -MF ".deps/fuse_mt.Tpo" -c -o fuse_mt.lo fuse_mt.c; \
        then mv -f ".deps/fuse_mt.Tpo" ".deps/fuse_mt.Plo"; else rm -f ".deps/fuse_mt.Tpo"; exit 1; fi
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT fuse_mt.lo -MD -MP -MF .deps/fuse_mt.Tpo -c fuse_mt.c  -fPIC -DPIC -o .libs/fuse_mt.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT fuse_mt.lo -MD -MP -MF .deps/fuse_mt.Tpo -c fuse_mt.c -o fuse_mt.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include  -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26   -Wall -W -g -O2 -MT fuse_opt.lo -MD -MP -MF ".deps/fuse_opt.Tpo" -c -o fuse_opt.lo fuse_opt.c; \
        then mv -f ".deps/fuse_opt.Tpo" ".deps/fuse_opt.Plo"; else rm -f ".deps/fuse_opt.Tpo"; exit 1; fi
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT fuse_opt.lo -MD -MP -MF .deps/fuse_opt.Tpo -c fuse_opt.c  -fPIC -DPIC -o .libs/fuse_opt.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT fuse_opt.lo -MD -MP -MF .deps/fuse_opt.Tpo -c fuse_opt.c -o fuse_opt.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include  -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26   -Wall -W -g -O2 -MT fuse_session.lo -MD -MP -MF ".deps/fuse_session.Tpo" -c -o fuse_session.lo fuse_session.c; \
        then mv -f ".deps/fuse_session.Tpo" ".deps/fuse_session.Plo"; else rm -f ".deps/fuse_session.Tpo"; exit 1; fi
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT fuse_session.lo -MD -MP -MF .deps/fuse_session.Tpo -c fuse_session.c  -fPIC -DPIC -o .libs/fuse_session.o
fuse_session.c: In function 'fuse_chan_recv':
fuse_session.c:179: warning: dereferencing type-punned pointer will break strict-aliasing rules
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT fuse_session.lo -MD -MP -MF .deps/fuse_session.Tpo -c fuse_session.c -o fuse_session.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include  -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26   -Wall -W -g -O2 -MT fuse_signals.lo -MD -MP -MF ".deps/fuse_signals.Tpo" -c -o fuse_signals.lo fuse_signals.c; \
        then mv -f ".deps/fuse_signals.Tpo" ".deps/fuse_signals.Plo"; else rm -f ".deps/fuse_signals.Tpo"; exit 1; fi
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT fuse_signals.lo -MD -MP -MF .deps/fuse_signals.Tpo -c fuse_signals.c  -fPIC -DPIC -o .libs/fuse_signals.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT fuse_signals.lo -MD -MP -MF .deps/fuse_signals.Tpo -c fuse_signals.c -o fuse_signals.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include  -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26   -Wall -W -g -O2 -MT helper.lo -MD -MP -MF ".deps/helper.Tpo" -c -o helper.lo helper.c; \
        then mv -f ".deps/helper.Tpo" ".deps/helper.Plo"; else rm -f ".deps/helper.Tpo"; exit 1; fi
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT helper.lo -MD -MP -MF .deps/helper.Tpo -c helper.c  -fPIC -DPIC -o .libs/helper.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT helper.lo -MD -MP -MF .deps/helper.Tpo -c helper.c -o helper.o >/dev/null 2>&1
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include  -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26   -Wall -W -g -O2 -MT mount.lo -MD -MP -MF ".deps/mount.Tpo" -c -o mount.lo mount.c; \
        then mv -f ".deps/mount.Tpo" ".deps/mount.Plo"; else rm -f ".deps/mount.Tpo"; exit 1; fi
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT mount.lo -MD -MP -MF .deps/mount.Tpo -c mount.c  -fPIC -DPIC -o .libs/mount.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT mount.lo -MD -MP -MF .deps/mount.Tpo -c mount.c -o mount.o >/dev/null 2>&1
/bin/bash ../libtool --tag=CC --mode=link gcc  -Wall -W -g -O2   -o libfuse.la -rpath /usr/local/lib -pthread -lrt  -version-number 2:6:0 -Wl,--version-script,./fuse_versionscript fuse.lo fuse_kern_chan.lo fuse_loop.lo fuse_loop_mt.lo fuse_lowlevel.lo fuse_mt.lo fuse_opt.lo fuse_session.lo fuse_signals.lo helper.lo mount.lo
libtool: link: gcc -shared  .libs/fuse.o .libs/fuse_kern_chan.o .libs/fuse_loop.o .libs/fuse_loop_mt.o .libs/fuse_lowlevel.o .libs/fuse_mt.o .libs/fuse_opt.o .libs/fuse_session.o .libs/fuse_signals.o .libs/helper.o .libs/mount.o   -lrt  -pthread -Wl,--version-script -Wl,./fuse_versionscript -Wl,-soname -Wl,libfuse.so.2 -o .libs/libfuse.so.2.6.0
libtool: link: (cd ".libs" && rm -f "libfuse.so.2" && ln -s "libfuse.so.2.6.0" "libfuse.so.2")
libtool: link: (cd ".libs" && rm -f "libfuse.so" && ln -s "libfuse.so.2.6.0" "libfuse.so")
libtool: link: ar cru .libs/libfuse.a  fuse.o fuse_kern_chan.o fuse_loop.o fuse_loop_mt.o fuse_lowlevel.o fuse_mt.o fuse_opt.o fuse_session.o fuse_signals.o helper.o mount.o
libtool: link: ranlib .libs/libfuse.a
libtool: link: creating libfuse.la
libtool: link: ( cd ".libs" && rm -f "libfuse.la" && ln -s "../libfuse.la" "libfuse.la" )
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include  -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26   -Wall -W -g -O2 -MT ulockmgr.lo -MD -MP -MF ".deps/ulockmgr.Tpo" -c -o ulockmgr.lo ulockmgr.c; \
        then mv -f ".deps/ulockmgr.Tpo" ".deps/ulockmgr.Plo"; else rm -f ".deps/ulockmgr.Tpo"; exit 1; fi
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT ulockmgr.lo -MD -MP -MF .deps/ulockmgr.Tpo -c ulockmgr.c  -fPIC -DPIC -o .libs/ulockmgr.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -DFUSERMOUNT_DIR=\"/usr/local/bin\" -D_FILE_OFFSET_BITS=64 -D_REENTRANT -DFUSE_USE_VERSION=26 -Wall -W -g -O2 -MT ulockmgr.lo -MD -MP -MF .deps/ulockmgr.Tpo -c ulockmgr.c -o ulockmgr.o >/dev/null 2>&1
/bin/bash ../libtool --tag=CC --mode=link gcc  -Wall -W -g -O2   -o libulockmgr.la -rpath /usr/local/lib -version-number 1:0:0 ulockmgr.lo
libtool: link: gcc -shared  .libs/ulockmgr.o    -Wl,-soname -Wl,libulockmgr.so.1 -o .libs/libulockmgr.so.1.0.0
libtool: link: (cd ".libs" && rm -f "libulockmgr.so.1" && ln -s "libulockmgr.so.1.0.0" "libulockmgr.so.1")
libtool: link: (cd ".libs" && rm -f "libulockmgr.so" && ln -s "libulockmgr.so.1.0.0" "libulockmgr.so")
libtool: link: ar cru .libs/libulockmgr.a  ulockmgr.o
libtool: link: ranlib .libs/libulockmgr.a
libtool: link: creating libulockmgr.la
libtool: link: ( cd ".libs" && rm -f "libulockmgr.la" && ln -s "../libulockmgr.la" "libulockmgr.la" )
make[1]: Leaving directory `/home/emil/Desktop/fuse-2.6.0/lib'
Making all in util
make[1]: Entering directory `/home/emil/Desktop/fuse-2.6.0/util'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include  -D_FILE_OFFSET_BITS=64    -Wall -W -g -O2 -MT fusermount.o -MD -MP -MF ".deps/fusermount.Tpo" -c -o fusermount.o fusermount.c; \
        then mv -f ".deps/fusermount.Tpo" ".deps/fusermount.Po"; else rm -f ".deps/fusermount.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -Wall -W -g -O2   -o fusermount  fusermount.o
libtool: link: gcc -Wall -W -g -O2 -o fusermount fusermount.o
if gcc -DHAVE_CONFIG_H -I. -I. -I../include  -D_FILE_OFFSET_BITS=64 -D_REENTRANT    -Wall -W -g -O2 -MT ulockmgr_server-ulockmgr_server.o -MD -MP -MF ".deps/ulockmgr_server-ulockmgr_server.Tpo" -c -o ulockmgr_server-ulockmgr_server.o `test -f 'ulockmgr_server.c' || echo './'`ulockmgr_server.c; \
        then mv -f ".deps/ulockmgr_server-ulockmgr_server.Tpo" ".deps/ulockmgr_server-ulockmgr_server.Po"; else rm -f ".deps/ulockmgr_server-ulockmgr_server.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -Wall -W -g -O2   -o ulockmgr_server -pthread ulockmgr_server-ulockmgr_server.o
libtool: link: gcc -Wall -W -g -O2 -o ulockmgr_server -pthread ulockmgr_server-ulockmgr_server.o
make[1]: Leaving directory `/home/emil/Desktop/fuse-2.6.0/util'
Making all in example
make[1]: Entering directory `/home/emil/Desktop/fuse-2.6.0/example'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include  -I../include -D_FILE_OFFSET_BITS=64 -D_REENTRANT   -Wall -W -g -O2 -MT fusexmp.o -MD -MP -MF ".deps/fusexmp.Tpo" -c -o fusexmp.o fusexmp.c; \
        then mv -f ".deps/fusexmp.Tpo" ".deps/fusexmp.Po"; else rm -f ".deps/fusexmp.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -Wall -W -g -O2   -o fusexmp  fusexmp.o ../lib/libfuse.la -lpthread
libtool: link: gcc -Wall -W -g -O2 -o .libs/fusexmp fusexmp.o  -pthread ../lib/.libs/libfuse.so -lrt -lpthread -Wl,-rpath -Wl,/usr/local/lib
libtool: link: creating fusexmp
if gcc -DHAVE_CONFIG_H -I. -I. -I../include  -I../include -D_FILE_OFFSET_BITS=64 -D_REENTRANT   -Wall -W -g -O2 -MT fusexmp_fh.o -MD -MP -MF ".deps/fusexmp_fh.Tpo" -c -o fusexmp_fh.o fusexmp_fh.c; \
        then mv -f ".deps/fusexmp_fh.Tpo" ".deps/fusexmp_fh.Po"; else rm -f ".deps/fusexmp_fh.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -Wall -W -g -O2   -o fusexmp_fh  fusexmp_fh.o ../lib/libfuse.la ../lib/libulockmgr.la -lpthread
libtool: link: gcc -Wall -W -g -O2 -o .libs/fusexmp_fh fusexmp_fh.o  ../lib/.libs/libfuse.so -lrt -pthread ../lib/.libs/libulockmgr.so -lpthread -Wl,-rpath -Wl,/usr/local/lib
libtool: link: creating fusexmp_fh
if gcc -DHAVE_CONFIG_H -I. -I. -I../include  -I../include -D_FILE_OFFSET_BITS=64 -D_REENTRANT   -Wall -W -g -O2 -MT null.o -MD -MP -MF ".deps/null.Tpo" -c -o null.o null.c; \
        then mv -f ".deps/null.Tpo" ".deps/null.Po"; else rm -f ".deps/null.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -Wall -W -g -O2   -o null  null.o ../lib/libfuse.la -lpthread
libtool: link: gcc -Wall -W -g -O2 -o .libs/null null.o  -pthread ../lib/.libs/libfuse.so -lrt -lpthread -Wl,-rpath -Wl,/usr/local/lib
libtool: link: creating null
if gcc -DHAVE_CONFIG_H -I. -I. -I../include  -I../include -D_FILE_OFFSET_BITS=64 -D_REENTRANT   -Wall -W -g -O2 -MT hello.o -MD -MP -MF ".deps/hello.Tpo" -c -o hello.o hello.c; \
        then mv -f ".deps/hello.Tpo" ".deps/hello.Po"; else rm -f ".deps/hello.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -Wall -W -g -O2   -o hello  hello.o ../lib/libfuse.la -lpthread
libtool: link: gcc -Wall -W -g -O2 -o .libs/hello hello.o  -pthread ../lib/.libs/libfuse.so -lrt -lpthread -Wl,-rpath -Wl,/usr/local/lib
libtool: link: creating hello
if gcc -DHAVE_CONFIG_H -I. -I. -I../include  -I../include -D_FILE_OFFSET_BITS=64 -D_REENTRANT   -Wall -W -g -O2 -MT hello_ll.o -MD -MP -MF ".deps/hello_ll.Tpo" -c -o hello_ll.o hello_ll.c; \
        then mv -f ".deps/hello_ll.Tpo" ".deps/hello_ll.Po"; else rm -f ".deps/hello_ll.Tpo"; exit 1; fi
/bin/bash ../libtool --tag=CC --mode=link gcc  -Wall -W -g -O2   -o hello_ll  hello_ll.o ../lib/libfuse.la -lpthread
libtool: link: gcc -Wall -W -g -O2 -o .libs/hello_ll hello_ll.o  -pthread ../lib/.libs/libfuse.so -lrt -lpthread -Wl,-rpath -Wl,/usr/local/lib
libtool: link: creating hello_ll
make[1]: Leaving directory `/home/emil/Desktop/fuse-2.6.0/example'
make[1]: Entering directory `/home/emil/Desktop/fuse-2.6.0'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/emil/Desktop/fuse-2.6.0'
root@Sandnabba: /home/emil/Desktop/fuse-2.6.0 # make install
Making install in kernel
make[1]: Entering directory `/home/emil/Desktop/fuse-2.6.0/kernel'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/emil/Desktop/fuse-2.6.0/kernel'
Making install in include
make[1]: Entering directory `/home/emil/Desktop/fuse-2.6.0/include'
make[2]: Entering directory `/home/emil/Desktop/fuse-2.6.0/include'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/fuse" || mkdir -p -- "/usr/local/include/fuse"
 /usr/bin/install -c -m 644 'fuse.h' '/usr/local/include/fuse/fuse.h'
 /usr/bin/install -c -m 644 'fuse_compat.h' '/usr/local/include/fuse/fuse_compat.h'
 /usr/bin/install -c -m 644 'fuse_common.h' '/usr/local/include/fuse/fuse_common.h'
 /usr/bin/install -c -m 644 'fuse_common_compat.h' '/usr/local/include/fuse/fuse_common_compat.h'
 /usr/bin/install -c -m 644 'fuse_lowlevel.h' '/usr/local/include/fuse/fuse_lowlevel.h'
 /usr/bin/install -c -m 644 'fuse_lowlevel_compat.h' '/usr/local/include/fuse/fuse_lowlevel_compat.h'
 /usr/bin/install -c -m 644 'fuse_opt.h' '/usr/local/include/fuse/fuse_opt.h'
test -z "/usr/local/include" || mkdir -p -- "/usr/local/include"
 /usr/bin/install -c -m 644 'old/fuse.h' '/usr/local/include/fuse.h'
 /usr/bin/install -c -m 644 'ulockmgr.h' '/usr/local/include/ulockmgr.h'
make[2]: Leaving directory `/home/emil/Desktop/fuse-2.6.0/include'
make[1]: Leaving directory `/home/emil/Desktop/fuse-2.6.0/include'
Making install in lib
make[1]: Entering directory `/home/emil/Desktop/fuse-2.6.0/lib'
make[2]: Entering directory `/home/emil/Desktop/fuse-2.6.0/lib'
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libfuse.la' '/usr/local/lib/libfuse.la'
libtool: install: /usr/bin/install -c .libs/libfuse.so.2.6.0 /usr/local/lib/libfuse.so.2.6.0
libtool: install: (cd /usr/local/lib && { ln -s -f libfuse.so.2.6.0 libfuse.so.2 || { rm -f libfuse.so.2 && ln -s libfuse.so.2.6.0 libfuse.so.2; }; })
libtool: install: (cd /usr/local/lib && { ln -s -f libfuse.so.2.6.0 libfuse.so || { rm -f libfuse.so && ln -s libfuse.so.2.6.0 libfuse.so; }; })
libtool: install: /usr/bin/install -c .libs/libfuse.lai /usr/local/lib/libfuse.la
libtool: install: /usr/bin/install -c .libs/libfuse.a /usr/local/lib/libfuse.a
libtool: install: chmod 644 /usr/local/lib/libfuse.a
libtool: install: ranlib /usr/local/lib/libfuse.a
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libulockmgr.la' '/usr/local/lib/libulockmgr.la'
libtool: install: /usr/bin/install -c .libs/libulockmgr.so.1.0.0 /usr/local/lib/libulockmgr.so.1.0.0
libtool: install: (cd /usr/local/lib && { ln -s -f libulockmgr.so.1.0.0 libulockmgr.so.1 || { rm -f libulockmgr.so.1 && ln -s libulockmgr.so.1.0.0 libulockmgr.so.1; }; })
libtool: install: (cd /usr/local/lib && { ln -s -f libulockmgr.so.1.0.0 libulockmgr.so || { rm -f libulockmgr.so && ln -s libulockmgr.so.1.0.0 libulockmgr.so; }; })
libtool: install: /usr/bin/install -c .libs/libulockmgr.lai /usr/local/lib/libulockmgr.la
libtool: install: /usr/bin/install -c .libs/libulockmgr.a /usr/local/lib/libulockmgr.a
libtool: install: chmod 644 /usr/local/lib/libulockmgr.a
libtool: install: ranlib /usr/local/lib/libulockmgr.a
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/emil/Desktop/fuse-2.6.0/lib'
make[1]: Leaving directory `/home/emil/Desktop/fuse-2.6.0/lib'
Making install in util
make[1]: Entering directory `/home/emil/Desktop/fuse-2.6.0/util'
make[2]: Entering directory `/home/emil/Desktop/fuse-2.6.0/util'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'fusermount' '/usr/local/bin/fusermount'
libtool: install: /usr/bin/install -c fusermount /usr/local/bin/fusermount
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'ulockmgr_server' '/usr/local/bin/ulockmgr_server'
libtool: install: /usr/bin/install -c ulockmgr_server /usr/local/bin/ulockmgr_server
mkdir -p -- /sbin
/usr/bin/install -c ./mount.fuse /sbin/mount.fuse
mkdir -p -- /etc/init.d
/usr/bin/install -c ./init_script /etc/init.d/fuse
/usr/sbin/update-rc.d fuse start 34 S . start 41 0 6 .
 System startup links for /etc/init.d/fuse already exist.
make  install-exec-hook
make[3]: Entering directory `/home/emil/Desktop/fuse-2.6.0/util'
chown root /usr/local/bin/fusermount
chmod u+s /usr/local/bin/fusermount
make[3]: Leaving directory `/home/emil/Desktop/fuse-2.6.0/util'
mkdir -p -- /etc/udev/rules.d
/usr/bin/install -c -m 644 ./udev.rules /etc/udev/rules.d/99-fuse.rules
make[2]: Leaving directory `/home/emil/Desktop/fuse-2.6.0/util'
make[1]: Leaving directory `/home/emil/Desktop/fuse-2.6.0/util'
Making install in example
make[1]: Entering directory `/home/emil/Desktop/fuse-2.6.0/example'
make[2]: Entering directory `/home/emil/Desktop/fuse-2.6.0/example'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/emil/Desktop/fuse-2.6.0/example'
make[1]: Leaving directory `/home/emil/Desktop/fuse-2.6.0/example'
make[1]: Entering directory `/home/emil/Desktop/fuse-2.6.0'
make[2]: Entering directory `/home/emil/Desktop/fuse-2.6.0'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pkgconfig" || mkdir -p -- "/usr/local/lib/pkgconfig"
 /usr/bin/install -c -m 644 'fuse.pc' '/usr/local/lib/pkgconfig/fuse.pc'
make[2]: Leaving directory `/home/emil/Desktop/fuse-2.6.0'
make[1]: Leaving directory `/home/emil/Desktop/fuse-2.6.0'

```

---

### Post by emil.s on 2006-10-30
And then:
```
emil@Sandnabba: ~/Desktop/siefs-0.5 $ make clean
Making clean in converter
make[1]: Entering directory `/home/emil/Desktop/siefs-0.5/converter'
test -z "vmo2wav" || rm -f vmo2wav
rm -f *.o core *.core
make[1]: Leaving directory `/home/emil/Desktop/siefs-0.5/converter'
Making clean in siefs
make[1]: Entering directory `/home/emil/Desktop/siefs-0.5/siefs'
test -z "siefs slink" || rm -f siefs slink
rm -f *.o core *.core
make[1]: Leaving directory `/home/emil/Desktop/siefs-0.5/siefs'
Making clean in .
make[1]: Entering directory `/home/emil/Desktop/siefs-0.5'
make[1]: Nothing to be done for `clean-am'.
make[1]: Leaving directory `/home/emil/Desktop/siefs-0.5'
emil@Sandnabba: ~/Desktop/siefs-0.5 $ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/emil/Desktop/siefs-0.5/missing: Unknown `--run' option
Try `/home/emil/Desktop/siefs-0.5/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for ranlib... ranlib
checking fuse installation... /usr/local
configure: creating ./config.status
config.status: creating Makefile
config.status: creating siefs/Makefile
config.status: creating converter/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
emil@Sandnabba: ~/Desktop/siefs-0.5 $ make
make  all-recursive
make[1]: Entering directory `/home/emil/Desktop/siefs-0.5'
Making all in siefs
make[2]: Entering directory `/home/emil/Desktop/siefs-0.5/siefs'
source='siefs.c' object='siefs.o' libtool=no \
        depfile='.deps/siefs.Po' tmpdepfile='.deps/siefs.TPo' \
        depmode=gcc3 /bin/bash ../depcomp \
        gcc -DHAVE_CONFIG_H -I. -I. -I..   -I/include  -I/usr/local/include -DFUSEINST="\"/usr/local\"" -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=22 -c `test -f 'siefs.c' || echo './'`siefs.c
siefs.c: In function ‘new_ascii2utf’:
siefs.c:102: warning: return makes pointer from integer without a cast
siefs.c: In function ‘getdir’:
siefs.c:132: warning: passing argument 1 of ‘new_ascii2utf’ discards qualifiers from pointer target type
siefs.c:139: warning: passing argument 1 of ‘free’ discards qualifiers from pointer target type
siefs.c:147: warning: passing argument 1 of ‘free’ discards qualifiers from pointer target type
siefs.c:168: warning: passing argument 1 of ‘free’ discards qualifiers from pointer target type
siefs.c: In function ‘siefs_getdir’:
siefs.c:177: warning: passing argument 1 of ‘new_ascii2utf’ discards qualifiers from pointer target type
siefs.c:179: warning: passing argument 1 of ‘free’ discards qualifiers from pointer target type
siefs.c: In function ‘siefs_getattr’:
siefs.c:191: warning: passing argument 1 of ‘new_ascii2utf’ discards qualifiers from pointer target type
siefs.c:230: warning: passing argument 1 of ‘free’ discards qualifiers from pointer target type
siefs.c: In function ‘siefs_mkdir’:
siefs.c:240: warning: passing argument 1 of ‘new_ascii2utf’ discards qualifiers from pointer target type
siefs.c:246: warning: passing argument 1 of ‘free’ discards qualifiers from pointer target type
siefs.c: In function ‘siefs_unlink’:
siefs.c:257: warning: passing argument 1 of ‘new_ascii2utf’ discards qualifiers from pointer target type
siefs.c:263: warning: passing argument 1 of ‘free’ discards qualifiers from pointer target type
siefs.c: In function ‘siefs_truncate’:
siefs.c:279: warning: passing argument 1 of ‘new_ascii2utf’ discards qualifiers from pointer target type
siefs.c:290: warning: passing argument 1 of ‘free’ discards qualifiers from pointer target type
siefs.c: In function ‘siefs_rename’:
siefs.c:301: warning: passing argument 1 of ‘new_ascii2utf’ discards qualifiers from pointer target type
siefs.c:302: warning: passing argument 1 of ‘new_ascii2utf’ discards qualifiers from pointer target type
siefs.c:308: warning: passing argument 1 of ‘free’ discards qualifiers from pointer target type
siefs.c:309: warning: passing argument 1 of ‘free’ discards qualifiers from pointer target type
siefs.c: In function ‘siefs_mknod’:
siefs.c:328: warning: passing argument 1 of ‘new_ascii2utf’ discards qualifiers from pointer target type
siefs.c:337: warning: passing argument 1 of ‘free’ discards qualifiers from pointer target type
siefs.c: In function ‘siefs_open’:
siefs.c:349: warning: passing argument 1 of ‘new_ascii2utf’ discards qualifiers from pointer target type
siefs.c:393: warning: passing argument 1 of ‘free’ discards qualifiers from pointer target type
siefs.c: In function ‘siefs_close’:
siefs.c:402: warning: passing argument 1 of ‘new_ascii2utf’ discards qualifiers from pointer target type
siefs.c:413: warning: passing argument 1 of ‘free’ discards qualifiers from pointer target type
siefs.c: In function ‘siefs_read’:
siefs.c:425: warning: passing argument 1 of ‘new_ascii2utf’ discards qualifiers from pointer target type
siefs.c:428: warning: passing argument 1 of ‘free’ discards qualifiers from pointer target type
siefs.c:437: warning: passing argument 1 of ‘free’ discards qualifiers from pointer target type
siefs.c:450: warning: passing argument 1 of ‘free’ discards qualifiers from pointer target type
siefs.c: In function ‘siefs_write’:
siefs.c:462: warning: passing argument 1 of ‘new_ascii2utf’ discards qualifiers from pointer target type
siefs.c:465: warning: passing argument 1 of ‘free’ discards qualifiers from pointer target type
siefs.c:470: warning: passing argument 1 of ‘free’ discards qualifiers from pointer target type
siefs.c:482: warning: passing argument 1 of ‘free’ discards qualifiers from pointer target type
source='obex.c' object='obex.o' libtool=no \
        depfile='.deps/obex.Po' tmpdepfile='.deps/obex.TPo' \
        depmode=gcc3 /bin/bash ../depcomp \
        gcc -DHAVE_CONFIG_H -I. -I. -I..   -I/include  -I/usr/local/include -DFUSEINST="\"/usr/local\"" -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=22 -c `test -f 'obex.c' || echo './'`obex.c
source='transport.c' object='transport.o' libtool=no \
        depfile='.deps/transport.Po' tmpdepfile='.deps/transport.TPo' \
        depmode=gcc3 /bin/bash ../depcomp \
        gcc -DHAVE_CONFIG_H -I. -I. -I..   -I/include  -I/usr/local/include -DFUSEINST="\"/usr/local\"" -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=22 -c `test -f 'transport.c' || echo './'`transport.c
transport.c: In function ‘tra_send’:
transport.c:353: warning: incompatible implicit declaration of built-in function ‘memcpy’
transport.c: In function ‘tra_recv’:
transport.c:478: warning: incompatible implicit declaration of built-in function ‘memcpy’
transport.c:486: warning: incompatible implicit declaration of built-in function ‘memcpy’
transport.c:496: warning: incompatible implicit declaration of built-in function ‘memcpy’
source='comm.c' object='comm.o' libtool=no \
        depfile='.deps/comm.Po' tmpdepfile='.deps/comm.TPo' \
        depmode=gcc3 /bin/bash ../depcomp \
        gcc -DHAVE_CONFIG_H -I. -I. -I..   -I/include  -I/usr/local/include -DFUSEINST="\"/usr/local\"" -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=22 -c `test -f 'comm.c' || echo './'`comm.c
comm.c: In function ‘comm_open’:
comm.c:54: warning: incompatible implicit declaration of built-in function ‘strdup’
comm.c: In function ‘comm_restore’:
comm.c:117: warning: incompatible implicit declaration of built-in function ‘bzero’
source='crcmodel.c' object='crcmodel.o' libtool=no \
        depfile='.deps/crcmodel.Po' tmpdepfile='.deps/crcmodel.TPo' \
        depmode=gcc3 /bin/bash ../depcomp \
        gcc -DHAVE_CONFIG_H -I. -I. -I..   -I/include  -I/usr/local/include -DFUSEINST="\"/usr/local\"" -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=22 -c `test -f 'crcmodel.c' || echo './'`crcmodel.c
source='charset.c' object='charset.o' libtool=no \
        depfile='.deps/charset.Po' tmpdepfile='.deps/charset.TPo' \
        depmode=gcc3 /bin/bash ../depcomp \
        gcc -DHAVE_CONFIG_H -I. -I. -I..   -I/include  -I/usr/local/include -DFUSEINST="\"/usr/local\"" -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=22 -c `test -f 'charset.c' || echo './'`charset.c
charset.c: In function ‘init_charset’:
charset.c:1189: warning: incompatible implicit declaration of built-in function ‘malloc’
gcc  -I/usr/local/include -DFUSEINST="\"/usr/local\"" -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=22  -L/lib -o siefs  siefs.o obex.o transport.o comm.o crcmodel.o charset.o /usr/local/lib/libfuse.a -lpthread
/usr/local/lib/libfuse.a(fuse.o): In function `curr_time':
/home/emil/Desktop/fuse-2.6.0/lib/fuse.c:738: undefined reference to `clock_gettime'
/home/emil/Desktop/fuse-2.6.0/lib/fuse.c:741: undefined reference to `clock_gettime'
collect2: ld returned 1 exit status
make[2]: *** [siefs] Error 1
make[2]: Leaving directory `/home/emil/Desktop/siefs-0.5/siefs'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/emil/Desktop/siefs-0.5'
make: *** [all] Error 2
```

---

