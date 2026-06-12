---
title: "Compiling Nautilus From Source"
date: 2007-08-06
forum: Packaging and Compiling Programs
---

### Post by fatsheep on 2007-08-06
I have compiled stuff from source before with the ./configure, make, and make install commands.  I want to install nautilus into a subdirectory with ./configure --prefix="$HOME/nautilus" Below are my results.

```
fatsheep:~/Programming/Compiling/nautilus-2.19.2$ ./configure --prefix="$HOME/nautilus"
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking whether byte ordering is bigendian... no
checking for an ANSI C-conforming const... yes
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognise dependent libraries... pass_all
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
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
***** WARNING: Building without libstartup-notification
checking pkg-config is at least version 0.9.0... yes
checking for ALL... configure: error: Package requirements (
        esound                  >= 0.2.27
        bonobo-activation-2.0   >= 2.1.0
        eel-2.0                 >= 2.15.91
        glib-2.0                >= 2.6.0
        gnome-desktop-2.0       >= 2.9.91
        gnome-vfs-2.0           >= 2.14.2
        gnome-vfs-module-2.0    >= 2.14.2
        ORBit-2.0               >= 2.4.0
        pango                   >= 1.1.2
        gtk+-2.0                >= 2.10.0
        libart-2.0              >= 2.3.10
        libbonobo-2.0           >= 2.1.0
        libgnome-2.0            >= 2.14.0
        libgnomeui-2.0          >= 2.6.0
        librsvg-2.0             >= 2.0.1
        libxml-2.0              >= 2.4.7

) were not met:

[B]No package 'esound' found
No package 'bonobo-activation-2.0' found
No package 'eel-2.0' found
No package 'gnome-desktop-2.0' found
No package 'gnome-vfs-2.0' found
No package 'gnome-vfs-module-2.0' found
No package 'ORBit-2.0' found
No package 'pango' found
No package 'gtk+-2.0' found
No package 'libart-2.0' found
No package 'libbonobo-2.0' found
No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'librsvg-2.0' found
No package 'libxml-2.0' found[/B]

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ALL_CFLAGS
and ALL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

fatsheep:~/Programming/Compiling/nautilus-2.19.2$ echo $PKG_CONFIG_PATH

fatsheep:~/Programming/Compiling/nautilus-2.19.2$ ./configure --help | grep PKG_CONFIG_PATH

```

As you can see, the variable $PKG_CONFIG_PATH is not set and there isn't anything on it in the ./configure --help message.  

What is strange is that most of this stuff on the list I have installed.  The "esound package" is definately installed:

> 
fatsheep:~$ dpkg -L esound
/.
/usr
/usr/bin
/usr/bin/esd
/usr/share
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/esd.1.gz
/usr/share/doc
/usr/share/doc/esound


Why can't the configure script find the package?  

Thanks,

-sheep

---

### Post by MrHippocampus on 2007-08-06
Youll need to install the *-dev packages (e.g. libesd0-dev for esound, synaptic will make your life easier for finding their names) for all of the packages listed, the *-dev packages hold all of the information needed for compiling.

---

### Post by fatsheep on 2007-08-06
> **MrHippocampus said:**
> Youll need to install the *-dev packages (e.g. libesd0-dev for esound, synaptic will make your life easier for finding their names) for all of the packages listed, the *-dev packages hold all of the information needed for compiling.

Thanks, installing libesd0-dev took care of the esound dependency but how on earth did you make the connection between esound and libesd0-dev?

---

### Post by fatsheep on 2007-08-06
> **MrHippocampus said:**
> Youll need to install the *-dev packages (e.g. libesd0-dev for esound, synaptic will make your life easier for finding their names) for all of the packages listed, the *-dev packages hold all of the information needed for compiling.

Thanks, installing libesd0-dev took care of the esound dependency but how on earth did you make the connection between esound and libesd0-dev?

EDIT: I did end up tracking down all the dependencies but I still would like to know how you found the esound dev package.

---

### Post by MrHippocampus on 2007-08-07
Well, there's probably a better way, but normally I do this:

Search in synaptic for the package I want and then see if it has a -dev version, if not, look at its immediate dependencies which start with "lib", these will most likely be the libraries that the package needs to run (normally named similar to the original package, sometimes an abbreviation). These lib* packages normally have -dev versions which will contain the files your after.

Its not elegant I know but it seems to work.

---

### Post by fatsheep on 2007-08-07
> **MrHippocampus said:**
> Well, there's probably a better way, but normally I do this:

Search in synaptic for the package I want and then see if it has a -dev version, if not, look at its immediate dependencies which start with "lib", these will most likely be the libraries that the package needs to run (normally named similar to the original package, sometimes an abbreviation). These lib* packages normally have -dev versions which will contain the files your after.

Its not elegant I know but it seems to work.

Well if it works, it works. :)  Thanks,

- sheep

---

### Post by RedSquirrel on 2007-08-08
If the package you want to compile is in the repositories, I would just run:

```
sudo apt-get build-dep package_name
```for that package (e.g., nautilus). That should install everything you need to compile... it works well for my fluxbox SVN builds anyway. :)  (check out the man page for apt-get)

---

### Post by manit on 2009-12-21
i suppose your tip is for users who want to install latest software from tarball if it has not yet arrived in repository.

---

