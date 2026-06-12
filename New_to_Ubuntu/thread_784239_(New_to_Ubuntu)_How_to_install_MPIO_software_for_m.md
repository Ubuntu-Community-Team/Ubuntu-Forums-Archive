---
title: "(New to Ubuntu) How to install MPIO software for my mp3 player?"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by kaunofrantas on 2008-05-06
So, I am completelly new to ubuntu. I have MPIO FL100 player and would like to install the software for it from [http://mpio.sourceforge.net/](http://mpio.sourceforge.net/)

Can anybody give my step-by-step instructions how to do it - both mpio software and kmpio software for graphical interface.

I tried to install it with alien but even though it put some stuff on my hard drive both on / and on my folder, I see no icons to run the software.

Do I need to unistall first? How do I do it?

Can you help?

Thanx.

---

### Post by JudasReanimated on 2008-05-06
Make sure you have the package build-essential downloaded and installed.

Download the program. Open Terminal.

```
tar zxvf "program here"
``` You can drag the archive file into the terminal for the address if you need.

Then

```
cd "Folder that you just extracted"
```

Then

```
./configure
```

```
make
```

```
sudo make install
```

That should do it. If you have an error then post it and let me know, as for Alien I don't remember right this second, but it's best to compile from source than ever convert RPM to Debian.

I'll check out Alien when I get home, but I don't use it much so I don't remember the exact commands for it ATM.

---

### Post by kaunofrantas on 2008-05-06
OK, so I was able to get to ./configure without error, then i get some compilation error. is there a way to fix it?

this is how it looks from terminal:

> kaunofrantas@kaunofrantas:~$ tar zxvf /home/kaunofrantas/Desktop/mpio-0.7.0.tar.gz 
mpio-0.7.0/
mpio-0.7.0/README
mpio-0.7.0/AUTHORS
mpio-0.7.0/COPYING
mpio-0.7.0/ChangeLog
mpio-0.7.0/INSTALL
mpio-0.7.0/Makefile.am
mpio-0.7.0/Makefile.in
mpio-0.7.0/NEWS
mpio-0.7.0/TODO
mpio-0.7.0/aclocal.m4
mpio-0.7.0/config.guess
mpio-0.7.0/config.sub
mpio-0.7.0/configure
mpio-0.7.0/configure.in
mpio-0.7.0/depcomp
mpio-0.7.0/install-sh
mpio-0.7.0/ltmain.sh
mpio-0.7.0/missing
mpio-0.7.0/mkinstalldirs
mpio-0.7.0/mpio.spec.in
mpio-0.7.0/mpio.spec
mpio-0.7.0/mkmpiodev
mpio-0.7.0/kernel/
mpio-0.7.0/kernel/Makefile.am
mpio-0.7.0/kernel/Makefile.in
mpio-0.7.0/kernel/mpio.c
mpio-0.7.0/libmpio/
mpio-0.7.0/libmpio/mplib/
mpio-0.7.0/libmpio/mplib/mplib.h
mpio-0.7.0/libmpio/mplib/mplib_s.h
mpio-0.7.0/libmpio/mplib/xmalloc.h
mpio-0.7.0/libmpio/mplib/mplib.c
mpio-0.7.0/libmpio/mplib/mplib_paas.c
mpio-0.7.0/libmpio/mplib/mplib_s.c
mpio-0.7.0/libmpio/mplib/xmalloc.c
mpio-0.7.0/libmpio/src/
mpio-0.7.0/libmpio/src/io.h
mpio-0.7.0/libmpio/src/smartmedia.h
mpio-0.7.0/libmpio/src/directory.h
mpio-0.7.0/libmpio/src/fat.h
mpio-0.7.0/libmpio/src/ecc.h
mpio-0.7.0/libmpio/src/cis.h
mpio-0.7.0/libmpio/src/id3.h
mpio-0.7.0/libmpio/src/mpio.c
mpio-0.7.0/libmpio/src/io.c
mpio-0.7.0/libmpio/src/debug.c
mpio-0.7.0/libmpio/src/smartmedia.c
mpio-0.7.0/libmpio/src/directory.c
mpio-0.7.0/libmpio/src/fat.c
mpio-0.7.0/libmpio/src/ecc.c
mpio-0.7.0/libmpio/src/cis.c
mpio-0.7.0/libmpio/src/id3.c
mpio-0.7.0/libmpio/debug.h
mpio-0.7.0/libmpio/mpio.h
mpio-0.7.0/libmpio/defs.h
mpio-0.7.0/libmpio/Makefile.am
mpio-0.7.0/libmpio/Makefile.in
mpio-0.7.0/mpiosh/
mpio-0.7.0/mpiosh/mpiosh.h
mpio-0.7.0/mpiosh/callback.h
mpio-0.7.0/mpiosh/readline.h
mpio-0.7.0/mpiosh/command.h
mpio-0.7.0/mpiosh/global.h
mpio-0.7.0/mpiosh/cfgio.h
mpio-0.7.0/mpiosh/config.h
mpio-0.7.0/mpiosh/Makefile.am
mpio-0.7.0/mpiosh/Makefile.in
mpio-0.7.0/mpiosh/mpiosh.c
mpio-0.7.0/mpiosh/callback.c
mpio-0.7.0/mpiosh/readline.c
mpio-0.7.0/mpiosh/command.c
mpio-0.7.0/mpiosh/global.c
mpio-0.7.0/mpiosh/cfgio.c
mpio-0.7.0/mpiosh/config.c
mpio-0.7.0/etc/
mpio-0.7.0/etc/Makefile.am
mpio-0.7.0/etc/Makefile.in
mpio-0.7.0/etc/mpioshrc
mpio-0.7.0/tools/
mpio-0.7.0/tools/Makefile.am
mpio-0.7.0/tools/Makefile.in
mpio-0.7.0/tools/mpiologo.c
kaunofrantas@kaunofrantas:~$ cd mpio-0.7.0
kaunofrantas@kaunofrantas:~/mpio-0.7.0$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
Building for a i686-pc-linux-gnu host.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.
kaunofrantas@kaunofrantas:~/mpio-0.7.0$ 

---

### Post by JudasReanimated on 2008-05-07
Looks like you may not have the compiler installed.

```
sudo aptitude install build-essential
```

Try that, then reconfigure.

---

### Post by kaunofrantas on 2008-05-07
Thanks for your patience. I installed compiler per your instructions but then get readline file error. I hope you can help:

> kaunofrantas@kaunofrantas:~/mpio-0.7.0$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
Building for a i686-pc-linux-gnu host.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
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
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking whether byte ordering is bigendian... no
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking readline/readline.h usability... no
checking readline/readline.h presence... no
checking for readline/readline.h... no
configure: error: could not find readline header files
kaunofrantas@kaunofrantas:~/mpio-0.7.0$ 

---

### Post by kaunofrantas on 2008-05-12
sorry bump up - can anyone help? thanks!

---

### Post by nomadddd on 2008-08-08
I had a similar problem trying to install the mpio software.  I was able to get past the readline error by installing the libreadline5-dev package.  You can do so by running sudo apt-get install libreadline5-dev.  I was able to build the make file but I got an error when trying to run the make file.  This was my error...

mpio.c:407:41: error: missing binary operator before token "("
mpio.c: In function ‘usb_mpio_cleanup’:
mpio.c:428: error: ‘struct mpio_usb_data’ has no member named ‘present’
mpio.c:629:41: error: missing binary operator before token "("
make[1]: *** [mpio.o] Error 1
make[1]: Leaving directory `/home/nomadddd/Desktop/mpio/mpio-0.7.0/kernel'
make: *** [all-recursive] Error 1


Let me know if you are able to get past this.  If I come up with anything I will let you know.

---

### Post by st33med on 2008-08-08
```
 sudo apt-get install linux-headers-2.6.24-19-generic 
```

---

### Post by nomadddd on 2008-08-08
Thanks for the advice but I am already at 2.6.24-19-generic.  Any other ideas?

---

### Post by JRBASTIEN on 2009-03-29
I would really like to be able to use my MPIO player again.

I have tried to installed the rpm package with Alien and got no error but I cannot even modprope the module. It does not seem installed.

So I decided to learn compilation.  I have installed the build-essential package, linux-headers-2.6.24-23-generic (which I'm using), libreadline5-dev, g++ (gnu c++ compiler) and g++ multilib and probably much more than I really needed. 

Although .configure does not report a direct error, I can see some in config.log ([ATTACH]108032[/ATTACH]:

configure:2693: gcc -c -g -O2  conftest.c >&5
conftest.c:2: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'me'
configure:2696: $? = 1
configure: failed program was:
| #ifndef __cplusplus
|   choke me
| #endif

If I run the make command, I get a series of failures like these:

Making all in kernel
make[1]: Entering directory `/usr/local/src/mpio-0.7.0/kernel'
gcc -c -D__KERNEL__ -Wall -Wstrict-prototypes -O2 -fomit-frame-pointer -pipe -DMODULE -I/lib/modules/2.6.24-23-generic/build/include mpio.c
In file included from /lib/modules/2.6.24-23-generic/build/include/asm/processor.h:4,
                 from /lib/modules/2.6.24-23-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.24-23-generic/build/include/linux/list.h:8,
                 from /lib/modules/2.6.24-23-generic/build/include/linux/module.h:9,
                 from mpio.c:37:
/lib/modules/2.6.24-23-generic/build/include/asm/processor_64.h:80: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/lib/modules/2.6.24-23-generic/build/include/asm/processor_64.h:80: error: requested alignment is not a constant
....

The closest solution I have found with Google is on this site:

[URL="http://perspex.com/hacks/linux/distros/mandrake/9.0/driver-barfs.html"]http://perspex.com/hacks/linux/distros/mandrake/9.0/driver-barfs.html
[/URL]
The guy says "Your sources and development tools are installed, but they're not primed.".  But the instruction are for Mandrake 9.0 September 2003.  That does not seem valid anymore for Ubuntu.

Anyone has a hint?  And you will have my eternal gratitude.

Thank you.

---

