---
title: "build and install the flashsupport library"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by myotis on 2008-10-01
I am trying to install the flashsupport library to use adobe.com.

The instructions are here [http://kb.adobe.com/selfservice/viewContent.do?externalId=kb403684&sliceId=2](http://kb.adobe.com/selfservice/viewContent.do?externalId=kb403684&sliceId=2)

I have tried to follow the instructions but have several errors. I have pasted the script below and would appreciate some help. You willl see I had a couple of false starts. Its Ubuntu 8.04

Thanks,

Graham


graham@T42-Linux:~$ sudo apt-get install automake libssl-dev libicu36-dev 
[sudo] password for graham: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libicu36-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libicu-dev
E: Package libicu36-dev has no installation candidate
graham@T42-Linux:~$ wget [http://downloads.sourceforge.net/flashsupport/flashsupport-9.0.1.tgz?modtime=1189805203&big_mirror=0](http://downloads.sourceforge.net/flashsupport/flashsupport-9.0.1.tgz?modtime=1189805203&big_mirror=0)
[1] 7951
graham@T42-Linux:~$ --17:07:26--  [http://downloads.sourceforge.net/flashsupport/flashsupport-9.0.1.tgz?modtime=1189805203](http://downloads.sourceforge.net/flashsupport/flashsupport-9.0.1.tgz?modtime=1189805203)
           => `flashsupport-9.0.1.tgz?modtime=1189805203'
Resolving downloads.sourceforge.net... 216.34.181.60
Connecting to downloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://kent.dl.sourceforge.net/sourceforge/flashsupport/flashsupport-9.0.1.tgz](http://kent.dl.sourceforge.net/sourceforge/flashsupport/flashsupport-9.0.1.tgz) [following]
--17:07:26--  [http://kent.dl.sourceforge.net/sourceforge/flashsupport/flashsupport-9.0.1.tgz](http://kent.dl.sourceforge.net/sourceforge/flashsupport/flashsupport-9.0.1.tgz)
           => `flashsupport-9.0.1.tgz'
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 301,552 (294K) [application/x-gzip]

100%[====================================>] 301,552      260.86K/s             

17:07:28 (259.99 KB/s) - `flashsupport-9.0.1.tgz' saved [301552/301552]

tar xvf flashsupport-9.0.1.tgz
flashsupport/
flashsupport/config.h.in
flashsupport/configure.ac
flashsupport/config.sub
flashsupport/configure
flashsupport/missing
flashsupport/config.guess
flashsupport/INSTALL
flashsupport/COPYING
flashsupport/install-sh
flashsupport/depcomp
flashsupport/ltmain.sh
flashsupport/flashsupport.c
flashsupport/Makefile.am
flashsupport/aclocal.m4
flashsupport/Makefile.in
flashsupport/autogen.sh
flashsupport/mkinstalldirs
[1]+  Done                    wget [http://downloads.sourceforge.net/flashsupport/flashsupport-9.0.1.tgz?modtime=1189805203](http://downloads.sourceforge.net/flashsupport/flashsupport-9.0.1.tgz?modtime=1189805203)
graham@T42-Linux:~$ cd flashsupport 
graham@T42-Linux:~/flashsupport$ #
graham@T42-Linux:~/flashsupport$ # sh configure 
graham@T42-Linux:~/flashsupport$ make
make: *** No targets specified and no makefile found. Stop.
graham@T42-Linux:~/flashsupport$ tar xvf flashsupport-9.0.1.tgz
tar: flashsupport-9.0.1.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
graham@T42-Linux:~/flashsupport$ cd
graham@T42-Linux:~$ tar xvf flashsupport-9.0.1.tgz
flashsupport/
flashsupport/config.h.in
flashsupport/configure.ac
flashsupport/config.sub
flashsupport/configure
flashsupport/missing
flashsupport/config.guess
flashsupport/INSTALL
flashsupport/COPYING
flashsupport/install-sh
flashsupport/depcomp
flashsupport/ltmain.sh
flashsupport/flashsupport.c
flashsupport/Makefile.am
flashsupport/aclocal.m4
flashsupport/Makefile.in
flashsupport/autogen.sh
flashsupport/mkinstalldirs
graham@T42-Linux:~$ cd flashsupport 
graham@T42-Linux:~/flashsupport$ sh configure 
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
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... gfortran
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether gfortran accepts -g... yes
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gfortran option to produce PIC... -fPIC
checking if gfortran PIC flag -fPIC works... yes
checking if gfortran static flag -static works... yes
checking if gfortran supports -c -o file.o... yes
checking whether the gfortran linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking openssl/ssl.h usability... no
checking openssl/ssl.h presence... no
checking for openssl/ssl.h... no
checking alsa/asoundlib.h usability... no
checking alsa/asoundlib.h presence... no
checking for alsa/asoundlib.h... no
checking linux/soundcard.h usability... yes
checking linux/soundcard.h presence... yes
checking for linux/soundcard.h... yes
checking linux/videodev.h usability... yes
checking linux/videodev.h presence... yes
checking for linux/videodev.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: executing depfiles commands
graham@T42-Linux:~/flashsupport$ make 
make  all-am
make[1]: Entering directory `/home/graham/flashsupport'
if /bin/bash ./libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -MT flashsupport.lo -MD -MP -MF ".deps/flashsupport.Tpo" \
	  -c -o flashsupport.lo `test -f 'flashsupport.c' || echo './'`flashsupport.c; \
	then mv -f ".deps/flashsupport.Tpo" ".deps/flashsupport.Plo"; \
	else rm -f ".deps/flashsupport.Tpo"; exit 1; \
	fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -MT flashsupport.lo -MD -MP -MF .deps/flashsupport.Tpo -c flashsupport.c  -fPIC -DPIC -o .libs/flashsupport.o
/bin/bash ./libtool --mode=link gcc  -g -O2   -o libflashsupport.la -rpath /usr/local/lib -version 9:0:0 -lssl -lpthread  flashsupport.lo  
gcc -shared  .libs/flashsupport.o  -lssl -lpthread  -Wl,-soname -Wl,libflashsupport.so.0 -o .libs/libflashsupport.so.0.0.0
/usr/bin/ld: cannot find -lssl
collect2: ld returned 1 exit status
make[1]: *** [libflashsupport.la] Error 1
make[1]: Leaving directory `/home/graham/flashsupport'
make: *** [all] Error 2
graham@T42-Linux:~/flashsupport$ cd
graham@T42-Linux:~$ sudo cp .libs/libflashsupport.so /usr/lib
[sudo] password for graham: 
cp: cannot stat `.libs/libflashsupport.so': No such file or directory
graham@T42-Linux:~$

---

### Post by echo314 on 2008-10-01
isn't there something similar in the repos, so you could just ```
sudo apt-get install libflashsupport
```

Or do a ```
apt-cache search libflash
``` and see what that shows up

---

### Post by myotis on 2008-10-01
> **echo314 said:**
> isn't there something similar in the repos, so you could just ```
sudo apt-get install libflashsupport
```

Or do a ```
apt-cache search libflash
``` and see what that shows up

There is libflash support in the repository and and apt-cache search libflash threw up flash support for Mozilla. I have installed these and things seem to be working.

As the adobe instructions specify they are for Ubuntu 8.04, I assumed that this meant this was the only way of doing it.

However, things seem to be working now at acrobat.com.

Thanks,

Graham

---

### Post by cariboo on 2008-10-01
Please mark this post as solved. If a website suggest compiling from source, always check the repositories using synaptic package manager first, as the software is probably already in the repositories. There are over 20,000 packages available, so if you can't find it, it is either really old and may not compile anyhow or it is bleeding edge and it still won't compile.

Jim

---

### Post by myotis on 2008-10-01
> **cariboo907 said:**
> Please mark this post as solved. If a website suggest compiling from source, always check the repositories using synaptic package manager first, as the software is probably already in the repositories. There are over 20,000 packages available, so if you can't find it, it is either really old and may not compile anyhow or it is bleeding edge and it still won't compile.

Jim

Now marked solved. I did check with synaptic first, but it wasn't at all obvious. the adobe instructions were about enabling SSL and the repository package said it was for enabling alsa with flash.

Graham

---

