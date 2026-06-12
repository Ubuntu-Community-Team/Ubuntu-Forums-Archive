---
title: "My first GUI applications"
date: 2006-04-16
forum: Programming Talk
---

### Post by Steveire on 2006-04-16
Hi.

I've just started using Kubuntu, and I'm new to linux.

I want to be able to create my own applications with a GUI. I'm comfortable enough with python and C++ that I'll be able to write the necessary back-end for either language. I have never coded with a GUI before, however, so this is where I need some assistance.

I am working with [this](http://www.kplug.org/glade_tutorial/glade2_tutorial/gtemp_4.html) tutorial for glade, and I have completed it without difficulty up to the page linked above. When I try to run autogen.sh, I get an error message:
```

steveire@ubuntu:~/Projects/gtemp$ ./autogen.sh
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... found 2.59
checking for automake = 1.4...
  testing automake-1.4... found 1.4
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.6
Checking for required M4 macros...
Checking for forbidden M4 macros...
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

Processing ./configure.in
Running libtoolize...
Running aclocal-1.4...
Running autoconf2.50...
Running autoheader2.50...
Running automake-1.4...
configure.in: 7: `automake requires `AM_CONFIG_HEADER', not `AC_CONFIG_HEADER'
steveire@ubuntu:~/Projects/gtemp$

```
I have searched for AM_CONFIG_HEADER in this forum and on the web, but I have not been able to find a solution for this issue. I suspect it's a case of knowing the answer or not, so hopefully someone else can help me.

I have:
[list]
[*]Kubuntu 5.10 - up to date
[*]glade-gnome-2 - version 2.12.0-0ubuntu1
[*]glademm - version 2.6.0-1
[*]libglade2-0
[*]libglade2-dev
[*]libglademm-2.4-1c2
[*]libglademm-2.4-dev
[*]libglademm-2.0-1
[*]libglademm-2.0-dev
[*]lots of libgtk2.0 packages
[/list]
and probably others. I've had this error from the beginning, and I've been installing all packages I think might help, but so far it's no use.

Can you help me solve this issue?

I thought that if I could get this working, I'd be able to make a simple app with C++. Something else I'd like to do is make applications that will work in windows. I assume that I'll be able to use the same or similar backend, and build the gui in a windows application with a windows.api or something. Is that correct? I'd like to code using python. Will that mean users will have to have python installed to run my application? I assume so as python is complied on the fly, and not as a binary.

If I can't get glade working, is there an alternative for me to use? (Not vim...)

Thanks for any replies.

Steve

---

### Post by Mr Egg on 2006-04-16
Well, for making GUI programs, I recommend using REALbasic ([http://realbasic.com)](http://realbasic.com)). The Linux version is free, and you can make some really good programs with it alot quicker than with Python or C++

---

### Post by nagilum on 2006-04-17
Have you tried fixing what the error message sais? Open the configure.in file and replace the AC_CONFIG_HEADER with AM_CONFIG_HEADER and the autogen.sh script should work fine. This is some autoconf / automake issue, in my own configure.in script I always use AM_CONFIG_HEADER. But don't ask me for some deeper insight, I'm constantly fighting with these tools myself.

As for writing cross-platform GUI applications GTK seems not to be the best choice. You can use it in Windows with cygwin but it doesn't run natively AFAIK. It will be a lot easier if you use a true cross-platform toolkit right from the start, something like [wxWidgets](http://www.wxwindows.org). Writing your own backends for each platform is of course also possible if like to invest that much work into this.
And yes, Python is an interpreted language, you must have Python installed to run your application.

I'm not sure what you mean by an alternative to Glade. Glade is just an interface designer, neither an editor nor an IDE. So it doesn't compare to Vim.

---

### Post by Steveire on 2006-04-17
```

steveire@ubuntu:~/Projects/gtemp$ ./autogen.sh
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... found 2.59
checking for automake = 1.4...
  testing automake-1.4... found 1.4
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.6
Checking for required M4 macros...
Checking for forbidden M4 macros...
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

Processing ./configure.in
Running libtoolize...
Running aclocal-1.4...
Running autoconf2.50...
configure.in:7: error: possibly undefined macro: AM_CONFIG_HEADERS
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.

```
I should have said that I already tried that. I got the above message, so I assumed I didn't have the macro and needed to install something to get it.

I edited configure.in to use the line
```

m4_pattern_allow(AM_CONFIG_HEADERS)

```
and now I get this: (fails sanity check)
```

steveire@ubuntu:~/Projects/gtemp$ ./autogen.sh
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... found 2.59
checking for automake = 1.4...
  testing automake-1.4... found 1.4
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.6
Checking for required M4 macros...
Checking for forbidden M4 macros...
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

Processing ./configure.in
Running libtoolize...
Running aclocal-1.4...
Running autoconf2.50...
Running automake-1.4...
configure.in: 7: required file `./config.h).in' not found
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... no
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... found
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking how to run the C preprocessor... gcc -E
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
steveire@ubuntu:~/Projects/gtemp$       

```

config.log is large and I don't know what to look for or what to change to make this work.

----------------
> 
As for writing cross-platform GUI applications GTK seems not to be the best choice. You can use it in Windows with cygwin but it doesn't run natively AFAIK. It will be a lot easier if you use a true cross-platform toolkit right from the start, something like wxWidgets. Writing your own backends for each platform is of course also possible if like to invest that much work into this.

I looked for wxwidgets in adept, and I seem to already have it( libwxgtk2.6-0) I think it was installed as a dependant package when I installed boa constructor, which I installed yesterday.
> Boa-constructor is an IDE oriented towards creating cross-platform applications built on top of the Python language and the WxWindows GUI toolkit.

It's cross platform, which is good, and I've already followed the tutorial with it to make a Notebook application. I'll look into py2exe.org to see about making a windows executable with the result. I tried that before without success, so we'll see...
I've just now got cx_freeze, so that might be what I need either.

Even though boa constructor seems to work well, I'd like to get Glade working (for coding in C++), so any pointer on the above error is welcome.

By alternative to glade, I mean another program I could use to make a GUI.

I'll check out realbasic too.

Thanks.

---

### Post by nagilum on 2006-04-17
[QUOTE=Steveire]
I should have said that I already tried that. I got the above message, so I assumed I didn't have the macro and needed to install something to get it.[/quote]
Ah, ok. Just saw a little detail, did you write AM_CONFIG_HEADER or AM_CONFIG_HEADERS (note the 's' at the end). It should be _HEADER, without the 's'.
If that doesn't help you could maybe attach the source to your next post, so I (or others) can experiment with it.

[QUOTE=Steveire]
config.log is large and I don't know what to look for or what to change to make this work.[/quote]
The part that caused the error is usually located at the end of the log, i.e. the last thing it did before bailing out.

[QUOTE=Steveire]
By alternative to glade, I mean another program I could use to make a GUI.
[/quote]
There's for example kdevelop for KDE/QT applications, though it's strongly directed at KDE.
If you can live with Java there's the Eclipse Platform. It brings along its own cross-platform GUI toolkit (SWT) which does more or less what you planned, it has backends to the native windowing toolkits on each platform like windows API, GTK and such. And there is an integrated GUI designer available.

---

### Post by GoldBuggie on 2006-04-17
I use either QT Designer or KDevelop for my GUI needs. QT Designer if I just want to concentrate on the GUI and then connect the program code later. KDevelop if I want a program that is more Visual Studio Like.

I only use qt with c++ which I think is a good combo but you could use PyQt and connect your gui from QT Designer with python code.

Good thing with using Qt is that platform independent. So linux, win or os x(mac) is all possible. I used it when writing a software project for a company that had both windows and os x.

---

### Post by jrib on 2006-04-17
[QUOTE=Steveire]Hi.
I have:
[list]
[*]Kubuntu 5.10 - up to date
[*]glade-gnome-2 - version 2.12.0-0ubuntu1
[*]glademm - version 2.6.0-1
[*]libglade2-0
[*]libglade2-dev
[*]libglademm-2.4-1c2
[*]libglademm-2.4-dev
[*]libglademm-2.0-1
[*]libglademm-2.0-dev
[*]lots of libgtk2.0 packages
[/list][/QUOTE]

Do you have build-essential?

---

### Post by Steveire on 2006-04-17
Thanks. I didn't. but now I do.
```

steveire@ubuntu:~/Projects/gtemp$ ./autogen.sh
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... found 2.59
checking for automake = 1.4...
  testing automake-1.4... found 1.4
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.6
Checking for required M4 macros...
Checking for forbidden M4 macros...
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

Processing ./configure.in
Running libtoolize...
Running aclocal-1.4...
Running autoconf2.50...
Running automake-1.4...
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... found
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
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
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
./configure: line 19763: GNOME_INIT: command not found
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes
checking what language compliance flags to pass to the C compiler...
Package libgnomemm-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgnomemm-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgnomemm-2.0' found
Package libgnomemm-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgnomemm-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgnomemm-2.0' found
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
Now type `make' to compile the package.
steveire@ubuntu:~/Projects/gtemp$ make
make: *** No rule to make target `@MAINTAINER_MODE_TRUE@', needed by `Makefile.in'.  Stop.
steveire@ubuntu:~/Projects/gtemp$      

```

I don't know what to do about this new error.

---

### Post by jrib on 2006-04-17
How about ```
apt-cache search libgnomemm
``` and see what turns up

---

### Post by Steveire on 2006-04-18
```

steveire@ubuntu:~$ apt-cache search libgnomemm
libgnomemm-2.6-1c2 - C++ wrappers for libgnome (shared library)
libgnomemm-2.6-dev - C++ wrappers for libgnome (development files)
libgnomemm-dev - C++ wrapper for GNOME 1 (development files)
libgnomemm1.2-9 - C++ wrapper for GNOME 1 (shared library)
libgnomemm2.0-1c2 - C++ wrappers for libgnome2 (development files)
libgnomemm2.0-dev - C++ wrappers for libgnome2 (shared library)
steveire@ubuntu:~$

```

I don't have any of those installed. Which do I need? Thanks for your help.

---

### Post by nagilum on 2006-04-18
Just found out something by chance, yesterday I tried to install some package from source and had to run the autogen.sh script as well. It did not succeed with automake-1.4 (same error as yours) but ran smoothly with automake-1.9. Maybe it solves your problem, too.

---

### Post by jrib on 2006-04-18
[QUOTE=Steveire]```

steveire@ubuntu:~$ apt-cache search libgnomemm
libgnomemm-2.6-1c2 - C++ wrappers for libgnome (shared library)
libgnomemm-2.6-dev - C++ wrappers for libgnome (development files)
libgnomemm-dev - C++ wrapper for GNOME 1 (development files)
libgnomemm1.2-9 - C++ wrapper for GNOME 1 (shared library)
libgnomemm2.0-1c2 - C++ wrappers for libgnome2 (development files)
libgnomemm2.0-dev - C++ wrappers for libgnome2 (shared library)
steveire@ubuntu:~$

```

I don't have any of those installed. Which do I need? Thanks for your help.[/QUOTE]
libgnomemm2.0-dev and maybe libgnomemm2.0-1c2 too?

it's in the ./configure output

---

