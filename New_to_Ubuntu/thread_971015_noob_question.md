---
title: "noob question"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by weesyboy on 2008-11-04
i installed 8.10 two days ago and have slowly been learning to use it, way way better that Microsoft anyway i have the nautilus bug 

"nautilus cannot handle "computer"/"network" locations

to fix it i have read that installing the gvfs from source will fix the problem but i get a error when i run ./configure

checking for DBUS... configure: error: Package requirements (dbus-1) were not met:

No package 'dbus-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DBUS_CFLAGS
and DBUS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

i have the dbus package installed

any help would be greatly appreciated thanks.

---

### Post by simtaalo on 2008-11-04
sorry i dont know how to fix the problem, but to get help more quickly please put a short description of the problem as the thread title, "noob question" doesnt really help.

something like "nautilus cannot handle "computer"/"network" locations" will ensure you get help quicker.

---

### Post by dracayr on 2008-11-04
well you have to install dbus. execute this in a terminal: ```
sudo apt-get install dbus libdbus-1-3 libdbus-1-dev
``` If you have other such unmet dependencies, use the command```
apt-cache search *package name*
``` to search for the package. For example, if you do apt-cache search dbus-1, this is (or should be) the output:```
libdbus-1-3 - simple interprocess messaging system
libdbus-1-dev - simple interprocess messaging system (development headers)
libdbus-1-qt3 - dbus bindings for Qt 3 (backport of the Qt 4 bindings)
libdbus-1-qt3-dev - dbus bindings for Qt 3 (backport of the Qt 4 bindings)

```

dracayr

---

### Post by weesyboy on 2008-11-05
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dbus is already the newest version.
libdbus-1-3 is already the newest version.
libdbus-1-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
:confused:

---

### Post by hyper_ch on 2008-11-05
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by weesyboy on 2008-11-05
well since the problem i'm having is not the nautilus thing its the install of the gvfs package so just to help i will post the whole output

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether build environment is sane... yes
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
checking for an ANSI C-conforming const... yes
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognize dependent libraries... pass_all
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
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
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
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/local/bin/pkg-config
checking whether gcc and cc understand -c and -o together... yes
checking for pid_t... yes
checking return type of signal handlers... void
checking for size_t... yes
checking for uid_t in sys/types.h... yes
checking for struct stat.st_mtimensec... no
checking for struct stat.st_mtim.tv_nsec... yes
checking for struct stat.st_atimensec... no
checking for struct stat.st_atim.tv_nsec... yes
checking for struct stat.st_ctimensec... no
checking for struct stat.st_ctim.tv_nsec... yes
checking pkg-config is at least version 0.9.0... yes
checking whether to build gtk-doc documentation... no
checking for gtkdoc-check... no
checking for GLIB... yes
checking for DBUS... configure: error: Package requirements (dbus-1) were not met:

No package 'dbus-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DBUS_CFLAGS
and DBUS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

and installing that package 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dbus is already the newest version.
libdbus-1-3 is already the newest version.
libdbus-1-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by dracayr on 2008-11-06
try configuring like this: ./configure --prefix="/usr"

If that doesn't work, you'll probably have to install dbus-1 from source also.

dracayr

---

### Post by weesyboy on 2008-11-07
yeah reinstalling dbus from source worked which subsequently fixed my nautilus problem.
:)

---

