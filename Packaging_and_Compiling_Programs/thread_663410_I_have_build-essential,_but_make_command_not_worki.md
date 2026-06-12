---
title: "I have build-essential, but make command not working"
date: 2008-01-10
forum: Packaging and Compiling Programs
---

### Post by SandyKhan on 2008-01-10
I have build-essential package, but there is still a problem with make command. When I run it in a directory, it shows following message:

mudassar@javaDev-1:~/Desktop/gwget-0.99$ make
make: *** No targets specified and no makefile found. Stop.

When I explicitly specify a make file, the following message appears:

mudassar@javaDev-1:~/Desktop/gwget-0.99$ make Makefile.in
make: Nothing to be done for `Makefile.in'.

Same message appears for all other files.

And, if I run install with make, it shows:

mudassar@javaDev-1:~/Desktop/gwget-0.99$ sudo make install
Password:
make: *** No rule to make target `install'. Stop.

Guide me how to use make in this scenario.

---

### Post by Perfect Storm on 2008-01-10
Please post the ./configure output.

---

### Post by SandyKhan on 2008-01-10
mudassar@javaDev-1:~/Desktop/gwget-0.99$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gconftool-2... /usr/bin/gconftool-2
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
checking for intltool >= 0.29... 0.35.5 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GNOME... configure: error: Package requirements (libgnomeui-2.0 >= 2.0.0
                          gtk+-2.0      >= 2.6.0
                          gmodule-2.0
                          libglade-2.0  >= 2.0.0
                          gnome-vfs-2.0
                          gnome-vfs-module-2.0) were not met:

No package 'libgnomeui-2.0' found
No package 'gtk+-2.0' found
No package 'gmodule-2.0' found
No package 'libglade-2.0' found
No package 'gnome-vfs-2.0' found
No package 'gnome-vfs-module-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOME_CFLAGS
and GNOME_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by Perfect Storm on 2008-01-10
You need to solve the missing libs before you can build it.

---

### Post by SandyKhan on 2008-01-10
I am not able to find what libs are missing. Are you talking about the following packages which are mentioned in ./configure output?

No package 'libgnomeui-2.0' found
No package 'gtk+-2.0' found
No package 'gmodule-2.0' found
No package 'libglade-2.0' found
No package 'gnome-vfs-2.0' found
No package 'gnome-vfs-module-2.0' found

---

### Post by Perfect Storm on 2008-01-10
No package 'libgnomeui-2.0' found = libgnomeui-dev
No package 'gtk+-2.0' found = libgtk2.0-dev
No package 'libglade-2.0' found = libglade2-dev
No package 'gnome-vfs-2.0' found = libgnomevfs2-dev

and so on...Use synaptic to find these packages.

---

### Post by Compyx on 2008-01-11
Is there some reason you need to install this from source? The package is in the universe repository of (at least) Gutsy.

So, a simple:
```

sudo apt-get install gwget

```
should do the trick.

If you really have to build it from source, you could try a:
```

sudo build-dep gwget

```
to install all libaries and headers needed to compile the package.

I can't check at the moment if any of this actually works, I'm at work behind a bloody M$-box. :(

---

### Post by dholbach on 2008-01-11
```
sudo apt-get build-dep gwget
```

---

### Post by Compyx on 2008-01-11
> **Compyx]```
sudo build-dep gwget
```[/QUOTE]
[QUOTE=dholbach said:**
> ```
sudo **apt-get** build-dep gwget
```

Whoops, I should drink more coffee before posting ;)

---

