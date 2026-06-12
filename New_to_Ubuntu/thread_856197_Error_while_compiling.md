---
title: "Error while compiling"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by sharks on 2008-07-11
I got a error while compiling compiz-0.7.6 on gutsy:

> arvind@ubuntu:~/Desktop/compiz-0.7.6$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
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
checking for intltool >= 0.23... 0.35.5 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... msgfmt
checking for msgmerge... msgmerge
checking for xgettext... xgettext
checking whether to enable maintainer-specific portions of Makefiles... no
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
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
checking the maximum length of command line arguments... 98304
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
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking for stdlib.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... no
checking whether byte ordering is bigendian... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for COMPIZ... configure: error: Package requirements (x11-xcb          xcomposite               xfixes                  xdamage                 xrandr                  xinerama                ice                     sm             libxml-2.0               libxslt                 libstartup-notification-1.0 >= 0.7) were not met:

No package 'x11-xcb' found
No package 'xcomposite' found
No package 'xfixes' found
No package 'xdamage' found
No package 'xrandr' found
No package 'xinerama' found
No package 'ice' found
No package 'sm' found
No package 'libxml-2.0' found
No package 'libxslt' found
No package 'libstartup-notification-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_CFLAGS
and COMPIZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

arvind@ubuntu:~/Desktop/compiz-0.7.6$

---

### Post by hyper_ch on 2008-07-11
and the question is?

---

### Post by ibutho on 2008-07-11
You need to search for those missing packages in Synaptic and install them as well as their dev versions.

---

### Post by sharks on 2008-07-11
how do i correct this and compile it successfully?

---

### Post by hyper_ch on 2008-07-11
have a look at the output... there's an error message that says what it lacks... you install that and it still complains, add teh ...-dev files also...

---

### Post by sharks on 2008-07-11
you mean libstartup-notification?

---

### Post by ibutho on 2008-07-11
> **sharks said:**
> you mean libstartup-notification?

All the ones listed as "no package" in the output in your first post.

---

### Post by sharks on 2008-07-11
please explain me about the installation. theres no package named like x11-xcb and many

---

### Post by ChameleonDave on 2008-07-11
> **sharks said:**
> No package 'x11-xcb' found
No package 'xcomposite' found
No package 'xfixes' found
No package 'xdamage' found
No package 'xrandr' found
No package 'xinerama' found
No package 'ice' found
No package 'sm' found
No package 'libxml-2.0' found
No package 'libxslt' found
No package 'libstartup-notification-1.0' found
It's really not hard to understand.

Search for each of those in Synaptic.  No, don't give up because you can't find the first one.  Search for all of them.  Install them.  Sometimes APT has some helpful suggestions.  For example:
```

david@Chameleon:~$ sudo apt-get install **xrandr**
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package xrandr is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  **x11-xserver-utils**
E: Package xrandr has no installation candidate

```Then search the web for .deb packages for the remaining ones.  No, don't give up because there is one you can't find a .deb for.  Look for the source code for packages that you absolutely cannot find.  Compile and install them.  Then try compiling this again.  Note any errors.  Rinse and repeat.

---

### Post by ibutho on 2008-07-11
> **sharks said:**
> please explain me about the installation. theres no package named like x11-xcb and many

If you search for xcb in synaptic, you will find a package called libx11-xcb-dev. Thats the one that you need to install.

---

### Post by vandorjw on 2008-07-17
Use this

>  sudo apt-get build-dep compiz

what this does, is exactly what it looks like.
It gets all the build dependencies for you to compile compiz.

Hope it helps.

PS: there are some packages where it will tell you it has found two.
Manually Select the newer one. / the one you need.

Then do it again

Cheers - CC7

(To compile from source)
Download the .gz.tar package from compiz,
extract it,  change directory to the folder.

and run ./configure

PS: you may need 
>  sudo apt-get install build-essential

---

