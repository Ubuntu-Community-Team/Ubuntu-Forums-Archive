---
title: "Problems compiling gDesklets from source"
date: 2005-05-03
forum: Packaging and Compiling Programs
---

### Post by derrick1985 on 2005-05-03
Hi, i'm getting this error when I try to install gDesklets from source:

```
configure: error: Library requirements (pygtk-2.0 >= 2.4.0 pyorbit-2 >= 2.0.1 gnome-python-2.0 >= 2.6.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
```

---

### Post by Fab on 2005-05-03
[QUOTE=derrick1985]Hi, i'm getting this error when I try to install gDesklets from source:

```
configure: error: Library requirements (pygtk-2.0 >= 2.4.0 pyorbit-2 >= 2.0.1 gnome-python-2.0 >= 2.6.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
```[/QUOTE]
 did you install the mentioned packages?

---

### Post by derrick1985 on 2005-05-03
[QUOTE=Fab]did you install the mentioned packages?[/QUOTE]

pygtk i can't find in synaptic,  and everything else i'm pretty sure  that I have. I might have higher versions than the ones listed though...

---

### Post by Fab on 2005-05-03
[QUOTE=derrick1985]pygtk i can't find in synaptic,  and everything else i'm pretty sure  that I have. I might have higher versions than the ones listed though...[/QUOTE]
 hmm, i dont remember exactly which packages i installed, but i suggest trying some connected to gtk + python.. i know i had problems with packages not mentioned in the README file

---

### Post by derrick1985 on 2005-05-04
[QUOTE=Fab]hmm, i dont remember exactly which packages i installed, but i suggest trying some connected to gtk + python.. i know i had problems with packages not mentioned in the README file[/QUOTE]

I seem to have all the packages from the readme file, here is the output i get:

derrick@ubuntu:~/gdesk/gDesklets-0.34.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking how to run the C++ preprocessor... gcc -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
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
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for more warnings... no
checking for a Python interpreter with version >= 2.3... python
checking for python... /usr/bin/python
checking for python version... 2.4
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.4/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.4/site-packages
checking /usr/include/python2.4/Python.h usability... yes
checking /usr/include/python2.4/Python.h presence... yes
checking for /usr/include/python2.4/Python.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking for pygtk-2.0 >= 2.4.0 pyorbit-2 >= 2.0.1 gnome-python-2.0 >= 2.6.0... Package ORBit-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `ORBit-2.0.pc'
to the PKG_CONFIG_PATH environment variable
Package 'ORBit-2.0', required by 'PyORBit', not found

configure: error: Library requirements (pygtk-2.0 >= 2.4.0 pyorbit-2 >= 2.0.1 gnome-python-2.0 >= 2.6.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
derrick@ubuntu:~/gdesk/gDesklets-0.34.3$

---

### Post by sebastyan on 2005-05-24
[QUOTE=derrick1985]Hi, i'm getting this error when I try to install gDesklets from source:

```
configure: error: Library requirements (pygtk-2.0 >= 2.4.0 pyorbit-2 >= 2.0.1 gnome-python-2.0 >= 2.6.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
```[/QUOTE]

Hello !
The same thing happened to me to
i have installed all required packages and the same error..... i duno what to do next ...
If anyone does .... let us know   :smile:

---

### Post by MemoryDump on 2005-06-07
[QUOTE=derrick1985]I seem to have all the packages from the readme file, here is the output i get:

checking for pygtk-2.0 >= 2.4.0 pyorbit-2 >= 2.0.1 gnome-python-2.0 >= 2.6.0... Package ORBit-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `ORBit-2.0.pc'
to the PKG_CONFIG_PATH environment variable
Package 'ORBit-2.0', required by 'PyORBit', not found

configure: error: Library requirements (pygtk-2.0 >= 2.4.0 pyorbit-2 >= 2.0.1 gnome-python-2.0 >= 2.6.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
derrick@ubuntu:~/gdesk/gDesklets-0.34.3$[/QUOTE]

has anyone found a fix for this yet? Now the that .35 is released I'd really like to get it install using it's source since it's not on the apt-get servers yet.

thxs
-MD

---

### Post by Lev on 2005-06-08
I had the same problem - solved by installing orbit (i thought i had it installed it at first, but it turned out to be pyorbit and not orbit... how pyorbit got installed without orbit im not quite sure)

Anyways - you can grab orbit from [http://www.gnome.org/projects/ORBit2/download.html](http://www.gnome.org/projects/ORBit2/download.html) and compile it. gDesklets .35 worked with it fine.

---

### Post by stubby on 2005-06-13
[QUOTE=MemoryDump]has anyone found a fix for this yet? Now the that .35 is released I'd really like to get it install using it's source since it's not on the apt-get servers yet.

thxs
-MD[/QUOTE]
 you'll need these packages as well

python2.4-dev
python-gtk2-dev
lib2orbit-dev
python-gnome2-dev
libgtop2-dev
librsvg2-dev
libgnomeui-dev

which are all in universe

---

### Post by Xian on 2005-06-13
The command below will check with the source file for the latest version available in APT and download/install the dependencies needed to compile it. They you should have everything you need to build the .35 version.

```
$ sudo apt-get build-dep gdesklets
```

---

### Post by Seth on 2005-06-15
[QUOTE=Xian]The command below will check with the source file for the latest version available in APT and download/install the dependencies needed to compile it. They you should have everything you need to build the .35 version.

```
$ sudo apt-get build-dep gdesklets
```[/QUOTE]
 Build-Depends: cdbs, debhelper (>> 4.1.65), python-dev (>= 2.4), python-gnome2-dev, python-gtk2-dev, libglib2.0-dev (>= 2.4.1-2), pkg-
config, swig, libgtk2.0-dev (>= 2.4.1-3), libgnomevfs2-dev (>= 2.6.1.1-3), libgtop2-dev (>= 2.9.4), gnome-pkg-tools, libgnomeui-dev (>
= 2.6.1.1-2), python2.4-pyorbit, libxml-parser-perl, librsvg2-dev

Here's gDesklets .35 for Hoary if you'd rather just use a .deb.
[http://ubuntuforums.org/showthread.php?t=40982](http://ubuntuforums.org/showthread.php?t=40982)

---

### Post by skazii on 2006-02-11
Hi..I did whatever was told..
and I get a problem using Gdesklets in Breezy:
make[2]: Leaving directory `/tmp/gDesklets-0.35.3'
make[1]: Leaving directory `/tmp/gDesklets-0.35.3'
root@ubuntu:/tmp/gDesklets-0.35.3# gdesklets

==========================================================[02/11/06-18:39:54]===The displaylist file has wrong format, ignoring it.


You must NOT run gDesklets as super user (root).
root@ubuntu:/tmp/gDesklets-0.35.3# su skazi
skazi@ubuntu:/tmp/gDesklets-0.35.3$ gdesklets
Starting gdesklets-daemon...
Connecting to daemon [  ###        ]Xlib: connection to ":0.0" refused by serverXlib: No protocol specified

Connecting to daemon [        ###  ]
Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.
skazi@ubuntu:/tmp/gDesklets-0.35.3$

I don't know what to do..Please help someone.
Thanks!

---

### Post by skazii on 2006-02-11
Hi..I did whatever was told..
and I get a problem using Gdesklets in Breezy:
make[2]: Leaving directory `/tmp/gDesklets-0.35.3'
make[1]: Leaving directory `/tmp/gDesklets-0.35.3'
root@ubuntu:/tmp/gDesklets-0.35.3# gdesklets

================================================== ========[02/11/06-18:39:54]===The displaylist file has wrong format, ignoring it.


You must NOT run gDesklets as super user (root).
root@ubuntu:/tmp/gDesklets-0.35.3# su skazi
skazi@ubuntu:/tmp/gDesklets-0.35.3$ gdesklets
Starting gdesklets-daemon...
Connecting to daemon [ ### ]Xlib: connection to ":0.0" refused by serverXlib: No protocol specified

Connecting to daemon [ ### ]
Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.
skazi@ubuntu:/tmp/gDesklets-0.35.3$

I don't know what to do..Please help someone.

---

### Post by YanalAlHasan on 2006-09-29
pygtk is actualy python-gtk so try to install python-gtk2-dev and python-gtk-1.2

Hope this helps.

---

### Post by dezine on 2007-07-21
> **Xian said:**
> The command below will check with the source file for the latest version available in APT and download/install the dependencies needed to compile it. They you should have everything you need to build the .35 version.

```
$ sudo apt-get build-dep gdesklets
```

Hey thanks this worked for me.

---

