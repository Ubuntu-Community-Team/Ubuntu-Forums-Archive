---
title: "Compiling SPIM"
date: 2008-02-13
forum: Programming Talk
---

### Post by ozzieball on 2008-02-13
Hello all,

I'm trying to compile SPIM/XSPIM for a class I'm currently taking. I originally installed SPIM via apt-get which worked great but my professor has developed a nifty add-on which requires me to compile SPIM manually so I can have the added functionality. I following the README on how to install/compile very carefully but for whatever reasons I get compile errors.

I start out and run ./Configure. This is the output:
```

 ./Configure
c++
Check if this machine is big-endian or little-endian.
This may take a few minutes.
I believe this is a little-endian machine.
Looks like a BSD universe exists...
Scaning libc
nm: old_atexit.o: no symbols
nm: udiv_qrnnd.o: no symbols
nm: mp_clz_tab.o: no symbols
nm: getopt_init.o: no symbols
nm: get_child_max.o: no symbols
nm: init-posix.o: no symbols
nm: lseek64.o: no symbols
nm: oldgetrlimit64.o: no symbols
nm: libc_multiple_threads.o: no symbols
nm: getutmpx.o: no symbols

Checking if libc on this machine contains:
  vsprintf: Yes, I think so
  vfprintf: Yes, I think
  strtoul: Yes, I think
  strtol: Yes, I think
  memcpy: Yes, I think

Checking for /usr/include/termio.h
Yes, it is there
```

Then I modify the Imakefile and used the following locations:

```
#
# The following parameters must be set for the target machine on which SPIM
# or XSPIM is compiled:
#

# Full path for directory that will hold the trap handler file:
TRAP_DIR = /usr/bin/

# Full path for the directory that will hold the executable files:
BIN_DIR = /usr/bin/

# Full path for the directory that will hold the man files:
MAN_DIR = /usr/lib/spim/
```

After that, it says run xmkmf, which I do and get:

```
xmkmf
mv -f Makefile Makefile.bak
imake -DUseInstalled -I/usr/lib/X11/config

```

So far all is well, then I go ahead and run make and get this garbage:

```
 make
make[1]: Entering directory `/home/brett/spimbot'
c++ -m32 -g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                                -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/bin//trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""    -c -o spim-utils.o spim-utils.c
c++ -m32 -g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                                -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/bin//trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""    -c -o run.o run.c
c++ -m32 -g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                                -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/bin//trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""    -c -o mem.o mem.c
c++ -m32 -g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                                -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/bin//trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""    -c -o inst.o inst.c
c++ -m32 -g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                                -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/bin//trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""    -c -o data.o data.c
c++ -m32 -g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                                -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/bin//trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""    -c -o sym-tbl.o sym-tbl.c
c++ -m32  -g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                               -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/bin//trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""   -c y.tab.c
c++ -m32  -g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                               -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/bin//trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""  -O -c lex.yy.c
c++ -m32 -g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                                -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/bin//trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""    -c -o mips-syscall.o mips-syscall.c
mips-syscall.c:166:1: warning: "REG_ERR" redefined
In file included from /usr/include/signal.h:351,
                 from mips-syscall.c:74:
/usr/include/sys/ucontext.h:70:1: warning: this is the location of the previous definition
c++ -m32 -g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                                -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/bin//trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""    -c -o display-utils.o display-utils.c
c++ -m32 -g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                                -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/bin//trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""    -c -o xspim.o xspim.c
c++ -m32 -g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                                -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/bin//trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""    -c -o windows.o windows.c
c++ -m32 -g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                                -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/bin//trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""    -c -o buttons.o buttons.c
c++ -m32 -g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                                -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/bin//trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""    -c -o robot.o robot.c
rm -f xspim_sub
c++ -m32 -o xspim_sub -g       spim-utils.o run.o mem.o inst.o data.o sym-tbl.o y.tab.o lex.yy.o mips-syscall.o display-utils.o xspim.o windows.o buttons.o robot.o -lXaw -lXmu -lXt -lSM -lICE -lXpm  -lXext -lX11   -lm   
make[1]: Leaving directory `/home/brett/spimbot'
mv xspim_sub spimbot
rm -f spim._man
if test -z "true" ; then \
           cd `dirname spim` && \
           ln -s `basename spim.man` `basename spim._man`; \
        else \
                     cpp -undef -traditional  -D__apploaddir__=/etc/X11/app-defaults -D__filemansuffix__=5x -D__osfilemansuffix__=5 -D__libmansuffix__=3x -D__oslibmansuffix__=3 -D__mansuffix__=1x -D__osmansuffix__=1 -D__syscallmansuffix__=2x -D__ossysmansuffix__=2 -D__gamemansuffix__=6x -D__osgamemansuffix__=6 -D__miscmansuffix__=7x -D__osmiscmansuffix__=7 -D__admmansuffix__=8x -D__osadmmansuffix__=8 -D__miscmansuffix__=7x -D__osmiscmansuffix__=7 -D__drivermansuffix__=4x -D__osdrivermansuffix__=4 -D__adminmansuffix__=8 -D__projectroot__=/usr -D__xconfigfile__=xorg.conf -D__xconfigdir__=/usr/lib/X11 -D__xlogfile__=Xorg -D__xservername__=Xorg -D__appmansuffix__=1x -D__xorgversion__="\"`echo 6 9 0 | sed -e 's/ /./g' -e 's/^/Version\\\ /'`\" \"X Version 11\"" -D__vendorversion__="`echo 6 9 0 | sed -e 's/ /./g' -e 's/^/Version\\\ /'` X.Org"  \
             < spim.man | sed -e '/^#  *[0-9][0-9]*  *.*$/d'                    -e '/^#line  *[0-9][0-9]*  *.*$/d'                      -e '/^[         ]*XCOMM$/s/XCOMM/#/'                    -e '/^[         ]*XCOMM[^a-zA-Z0-9_]/s/XCOMM/#/'                     -e '/^[         ]*XHASH/s/XHASH/#/'                     -e '/\@\@$/s/\@\@$/\\/' >spim._man; \
        fi
rm -f xspim._man
if test -z "true" ; then \
           cd `dirname xspim` && \
           ln -s `basename xspim.man` `basename xspim._man`; \
        else \
                     cpp -undef -traditional  -D__apploaddir__=/etc/X11/app-defaults -D__filemansuffix__=5x -D__osfilemansuffix__=5 -D__libmansuffix__=3x -D__oslibmansuffix__=3 -D__mansuffix__=1x -D__osmansuffix__=1 -D__syscallmansuffix__=2x -D__ossysmansuffix__=2 -D__gamemansuffix__=6x -D__osgamemansuffix__=6 -D__miscmansuffix__=7x -D__osmiscmansuffix__=7 -D__admmansuffix__=8x -D__osadmmansuffix__=8 -D__miscmansuffix__=7x -D__osmiscmansuffix__=7 -D__drivermansuffix__=4x -D__osdrivermansuffix__=4 -D__adminmansuffix__=8 -D__projectroot__=/usr -D__xconfigfile__=xorg.conf -D__xconfigdir__=/usr/lib/X11 -D__xlogfile__=Xorg -D__xservername__=Xorg -D__appmansuffix__=1x -D__xorgversion__="\"`echo 6 9 0 | sed -e 's/ /./g' -e 's/^/Version\\\ /'`\" \"X Version 11\"" -D__vendorversion__="`echo 6 9 0 | sed -e 's/ /./g' -e 's/^/Version\\\ /'` X.Org"  \
             < xspim.man | sed -e '/^#  *[0-9][0-9]*  *.*$/d'                   -e '/^#line  *[0-9][0-9]*  *.*$/d'                      -e '/^[         ]*XCOMM$/s/XCOMM/#/'                    -e '/^[         ]*XCOMM[^a-zA-Z0-9_]/s/XCOMM/#/'                     -e '/^[         ]*XHASH/s/XHASH/#/'                     -e '/\@\@$/s/\@\@$/\\/' >xspim._man; \
        fi

```

I made sure I have all the necessary dependencies and I'm thinking that's what ./Configure does. I've tried various things but nothing seems to work. I am thinking my error comes from where I'm telling SPIM my pathnames are. Can anyone offer any help, I'm quite frustrated and really curious as to how this is supposed to work. I also uninstalled SPIM thinking that might affect something, but I get nothing.

---

### Post by lnostdal on 2008-02-13
i see a warning but not an error message

---

### Post by ozzieball on 2008-02-13
> **lnostdal said:**
> i see a warning but not an error message

Yeah that is true. When I do a **make install** I get this, which I am assuming is where the errors are

```
make[1]: Entering directory `/home/brett/spimbot'
g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                          -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/lib/trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""    -c -o spim.o spim.c
/bin/sh: g: not found
make[1]: [spim.o] Error 127 (ignored)
g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                          -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/lib/trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""    -c -o spim-utils.o spim-utils.c
/bin/sh: g: not found
make[1]: [spim-utils.o] Error 127 (ignored)
g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                          -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/lib/trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""    -c -o run.o run.c
/bin/sh: g: not found
make[1]: [run.o] Error 127 (ignored)
g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                          -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/lib/trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""    -c -o mem.o mem.c
/bin/sh: g: not found
make[1]: [mem.o] Error 127 (ignored)
g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                          -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/lib/trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""    -c -o inst.o inst.c
/bin/sh: g: not found
make[1]: [inst.o] Error 127 (ignored)
g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                          -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/lib/trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""    -c -o data.o data.c
/bin/sh: g: not found
make[1]: [data.o] Error 127 (ignored)
g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                          -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/lib/trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""    -c -o sym-tbl.o sym-tbl.c
/bin/sh: g: not found
make[1]: [sym-tbl.o] Error 127 (ignored)
g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                          -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/lib/trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""   -c y.tab.c
/bin/sh: g: not found
make[1]: [y.tab.o] Error 127 (ignored)
g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                          -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/lib/trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""  -O -c lex.yy.c
/bin/sh: g: not found
make[1]: [lex.yy.o] Error 127 (ignored)
g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                          -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/lib/trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""    -c -o mips-syscall.o mips-syscall.c
/bin/sh: g: not found
make[1]: [mips-syscall.o] Error 127 (ignored)
g         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                          -D_POSIX_SOURCE -D_XOPEN_SOURCE                                 -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                                -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_TRAP_HANDLER=\"/usr/lib/trap.handler\" -DSPIM_VERSION="\"`cat VERSION`\""    -c -o display-utils.o display-utils.c
/bin/sh: g: not found
make[1]: [display-utils.o] Error 127 (ignored)
rm -f spim_sub
o spim_sub -g       spim.o spim-utils.o run.o mem.o inst.o data.o sym-tbl.o y.tab.o lex.yy.o mips-syscall.o display-utils.o    -lm   
/bin/sh: o: not found
make[1]: [spim_sub] Error 127 (ignored)
make[1]: Leaving directory `/home/brett/spimbot'
mv spim_sub spim
mv: cannot stat `spim_sub': No such file or directory
make: *** [spim] Error 1

```

One thing the README says that I'm thinking maybe an issue but don't know because I'm not well versed in Makefiles is:

> The main 
difference is that we've found it necessary to use a C++ compiler to compile the source, so the Imakefile defines CC in terms of CXX.

I was under the understand then that wherever it has a CC it will replace with CXX. Is that the case? If so, is that a valid argument?

---

### Post by vanduc1102 on 2009-10-05
I see how to install it in:

[http://pierrelucbacon.com/2009/01/05/installing-spimxspim/comment-page-1/#comment-703](http://pierrelucbacon.com/2009/01/05/installing-spimxspim/comment-page-1/#comment-703)

**Installing Spim/Xspim**

   Spim is A MIPS32 Simulator freely available for Linux, Mac and Windows. The process for installing the software from source is not as nice as we would expect it to be.
Download source code from:
[http://www.cs.wisc.edu/~larus/SPIM/spim.tar.gz](http://www.cs.wisc.edu/~larus/SPIM/spim.tar.gz)
 You will probably need to get Bison and Flex:
  [COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-get**[/COLOR] [COLOR=#C20CB9]**install**[/COLOR] [COLOR=#C20CB9]**bison**[/COLOR] [COLOR=#C20CB9]**flex**[/COLOR]

  Don’t forget:
  [COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-get**[/COLOR] [COLOR=#C20CB9]**install**[/COLOR] libxaw7-dev

  Otherwise you’ll get “X11/Xaw/Cardinals.h: No such file or directory”
 Build and install xspim first:
  [COLOR=#7A0874]**cd**[/COLOR] xspim; [COLOR=#C20CB9]**make**[/COLOR] [COLOR=#000000]**&**[/COLOR]amp;[COLOR=#000000]**&**[/COLOR]amp; [COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**make**[/COLOR] [COLOR=#C20CB9]**install**[/COLOR]

  Then spim:
  [COLOR=#7A0874]**cd**[/COLOR] ..[COLOR=#000000]**/**[/COLOR]spim; [COLOR=#C20CB9]**make**[/COLOR] [COLOR=#000000]**&**[/COLOR]amp;[COLOR=#000000]**&**[/COLOR]amp; [COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**make**[/COLOR] [COLOR=#C20CB9]**install**[/COLOR]

  If you install spim before xspim, the latter will fail with “install: accessing `/usr/lib/spim/exceptions.s’: Not a directory”

---

### Post by vinodvvk on 2011-02-11
Hi,
I am gonna work with MIPS in near future. I am assigned with the work of exploring simulator for MIPS. I tried SPIM but not sure how to work with that. I am desperately in need of your help.

1. I found SPIM supports only assembly language. I need to use C code as well. Is there any cross compiler which can be used along with SPIM to convert my C code to assembly language.
2. Is it possible to execute more than one file(.s files) in SPIM??
3. Is it possible to create new work space instead of directly opening a file
4. Is SPIM obsolete or it can be used for MIPS??

thanks in advance.

Regards,
[COLOR=#888888]vinod[/COLOR]

---

