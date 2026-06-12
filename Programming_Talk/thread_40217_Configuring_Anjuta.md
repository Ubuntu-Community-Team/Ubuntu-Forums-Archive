---
title: "Configuring Anjuta"
date: 2005-06-08
forum: Programming Talk
---

### Post by Zingam on 2005-06-08
Hmmm... I installed Anjuta with Synaptic but I cannot make it to generate a project with the Wizzard: I get this error: 

config.status: creating Makefile
config.status: error: cannot find input file: intl/Makefile.in

Any ideas? I have installed some dev-s for GNOME2, GTK

---

### Post by psychicdragon on 2005-06-08
My guess is that you haven't got build-essential installed. You may also need automake, I'm not sure.

sudo apt-get install build-essential automake

Try generating a project after you've got those installed. I think that should be everything you need but I'm not 100% sure :roll:

---

### Post by Zingam on 2005-06-09
This is the error output: I have them installed:
root@roccoor:/home/hristo # apt-get install automake
Reading package lists... Done
Building dependency tree... Done
Note, selecting automake1.4 instead of automake
automake1.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@roccoor:/home/hristo # apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by pietro_spina on 2005-06-14
do you have Smeg installed? If you do, I beleive it has some compatibility issues with a dev library or two... makes anjuta sad...

[The fix is here](http://ubuntuforums.org/showthread.php?p=187022) 

then i beleive yoiu can install the updated smeg from backports

but then this might have nothing to do with your problem anyway... hehehe

cheers,
p

---

### Post by Zingam on 2005-06-17
Here is a full log.

Note these lines:
[COLOR=DarkOrange]
[B]Running automake --gnu  ...
configure.in:105: required file `intl/Makefile.in' not found
configure.in:33: required file `./ABOUT-NLS' not found
Makefile.am:6: required directory ./intl does not exist


config.status: error: cannot find input file: Makefile.in[/B][/COLOR]


The log

[COLOR=Red]
hristo@roccoor:~/Projects/Proj1$ sh autogen.sh
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`autogen.sh' command line.

processing .
Creating ./aclocal.m4 ...
Running gettextize...  Ignore non-fatal messages.
  autopoint --force
autopoint: *** cvs program not found
autopoint: *** Stop.
Making ./aclocal.m4 writable ...
Running libtoolize...
Running aclocal  ...
/usr/share/aclocal/vorbis.m4:9: warning: underquoted definition of XIPH_PATH_VORBIS
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
/usr/share/aclocal/smpeg.m4:13: warning: underquoted definition of AM_PATH_SMPEG/usr/share/aclocal/pkg.m4:5: warning: underquoted definition of PKG_CHECK_MODULES
/usr/share/aclocal/aalib.m4:12: warning: underquoted definition of AM_PATH_AALIBRunning autoheader...
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader:
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows to define a template without
autoheader: WARNING: `acconfig.h':
autoheader:
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader:             [Define if a function `main' is needed.])
autoheader:
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
Running automake --gnu  ...
configure.in:105: required file `intl/Makefile.in' not found
configure.in:33: required file `./ABOUT-NLS' not found
Makefile.am:6: required directory ./intl does not exist
Running autoconf ...
Running ./configure ...
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
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 gdk-2.0... yes
checking GTK_CFLAGS... -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include
checking GTK_LIBS... -lgtk-x11-2.0 -latk-1.0 -lgdk-x11-2.0 -lgdk_pixbuf-2.0 -lm -lpangoxft-1.0 -lpangox-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for ranlib... (cached) ranlib
checking for an ANSI C-conforming const... yes
checking for signed... yes
checking for inline... inline
checking for off_t... yes
checking for size_t... yes
checking for long long... yes
checking for long double... yes
checking for wchar_t... yes
checking for wint_t... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for intmax_t... yes
checking whether printf() supports POSIX/XSI format strings... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether we are using the GNU C Library 2.1 or newer... yes
checking whether integer division by zero raises SIGFPE... yes
checking for unsigned long long... yes
checking for inttypes.h... yes
checking whether the inttypes.h PRIxNN macros are broken... no
checking for stdint.h... (cached) yes
checking for SIZE_MAX... yes
checking for stdint.h... (cached) yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... /bin/sh: ./config.rpath: No such file or directory
done
checking for ptrdiff_t... yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking nl_types.h usability... yes
checking nl_types.h presence... yes
checking for nl_types.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for asprintf... yes
checking for fwprintf... yes
checking for getcwd... yes
checking for getegid... yes
checking for geteuid... yes
checking for getgid... yes
checking for getuid... yes
checking for mempcpy... yes
checking for munmap... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for snprintf... yes
checking for stpcpy... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strtoul... yes
checking for tsearch... yes
checking for wcslen... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for __fsetlocking... yes
checking whether _snprintf is declared... no
checking whether _snwprintf is declared... no
checking whether feof_unlocked is declared... yes
checking whether fgets_unlocked is declared... no
checking whether getc_unlocked is declared... yes
checking for iconv... yes
checking for iconv declaration...
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo and CODESET... yes
checking for LC_MESSAGES... yes
checking for bison... no
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
configure: creating ./config.status
config.status: error: cannot find input file: Makefile.in[/COLOR]

---

### Post by pietro_spina on 2005-06-17
What kind of project did you specify in the wizard? Is it just the most basic? (console program ) or one of the others?

My Anjuta failed until I installed the g++ package... Even though I was specifying a "C" only project... sorry I can't be much more help...

Have you tried re-installing Anjuta and her dependencies through Synaptic?(I know, you probably have...but I had to ask...)


:)

-p

---

### Post by Zingam on 2005-06-20
It seems that automake is not working properly. Does it require any special configuration other than installing it via Synaptic?

---

### Post by pietro_spina on 2005-06-20
[QUOTE=Zingam]It seems that automake is not working properly. Does it require any special configuration other than installing it via Synaptic?[/QUOTE]

I didn't have to do anything special other than selecting to install most of the recommended and suggested dependencies for Anjuta.... Synaptic doesn't auto-magically do that... 

One other thought I had was that you should check to see what repository you installed this all from... I have my synaptic preferences set so that the package properties are displayed below the package list. 

Look at the tab called Version(I believe) and see if your repository list is giving you multiple versions available... see if you have installed from merrilat or something...

alternatively you could just comment out any non-official Ubuntu repositories like merrilat and backports... (just keep the main universe multiverse etc)

then apt-get update and apt-get install the stuff 
or do all this with synaptic...

cheers,
p

---

### Post by Burkey on 2005-06-21
Well, I get the exact same thing!! Arr, I went KDE and could not get KDevelop working properly, now I am back in Gnome and Anjuta is doing this.

So I am hoping you got it worked out and can tell me what is missing?

---

### Post by pravin on 2005-06-21
You need to install Internationalization package (the one that makes the po files). I can't recall its name right now and I'm not on an Ubuntu machine.

---

### Post by Zingam on 2005-06-22
[QUOTE=pravin]You need to install Internationalization package (the one that makes the po files). I can't recall its name right now and I'm not on an Ubuntu machine.[/QUOTE]

I have the gettext packages installed. What else do I need? Reinstalling Anjuta does not help.

Is there any other C++ IDE besides Anjuta and KDE I could youse?

---

### Post by pietro_spina on 2005-06-24
[QUOTE=Zingam]Is there any other C++ IDE besides Anjuta and KDE I could youse?[/QUOTE]

There is Eclipse. And I beleive there is a module or pluging (whatever they call it) for C and C++. but from what I hhear it has not reached the sophistication of their Java tools... people seem to love Eclipse for Java though...

I had an issue that I could not compile a C++ project and Anjuta wasn't finding /sbin/sh G++  and could see that this file didn't exist... I had installed "G++-3.3" and untill I installed the dependancy package"G++" I would get compile time errors...

Maybe it provides some links or something... but what I am getting at is you might want to make sure you have the "dependancy" packages installed

> Package: anjuta
Priority: optional
Section: universe/gnome
Installed-Size: 2048
Maintainer: Rob Bradford <robster@debian.org>
Architecture: i386
Version: 1.2.2-6ubuntu1
Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), libaudiofile0 (>= 0.2.3-4), libbonobo2-0 (>= 2.8.0), libbonoboui2-0 (>= 2.5.4), libc6 (>= 2.3.2.ds1-4), libesd0 (>= 0.2.29-1) | libesd-alsa0 (>= 0.2.29-1), libfontconfig1 (>= 2.2.1), libfreetype6 (>= 2.1.5-1), libgcc1 (>= 1:4.0-0pre6ubuntu4), libgconf2-4 (>= 2.9), libgcrypt11, libglade2-0 (>= 1:2.5.1), libglib2.0-0 (>= 2.6.0), libgnome-keyring0 (>= 0.4.0), libgnome2-0 (>= 2.8.0), libgnomecanvas2-0 (>= 2.6.0), libgnomeprint2.2-0 (>= 2.10.0), libgnomeprintui2.2-0 (>= 2.10.0), libgnomeui-0 (>= 2.8.0), libgnomevfs2-0 (>= 2.9.90), libgnutls11 (>= 1.0.16), libgpg-error0 (>= 1.0), libgtk2.0-0 (>= 2.6.0), libice6 | xlibs (>> 4.1.0), libjpeg62, libncurses5 (>= 5.4-1), liborbit2 (>= 1:2.12.0), libpango1.0-0 (>= 1.8.1), libpcre3 (>= 4.5), libpopt0 (>= 1.7), libsm6 | xlibs (>> 4.1.0), libstdc++5 (>= 1:3.3.4-1), libtasn1-2 (>= 0.2.8), libvte4 (>= 1:0.11.12), libx11-6 | xlibs (>> 4.1.0), libxft2 (>> 2.1.1), libxml2 (>= 2.6.17), libxrender1, zlib1g (>= 1:1.2.1), scrollkeeper, anjuta-common (>= 1.2.2)
Recommends: gcc | g++, make, cvs, gnome-terminal, yelp, automake, autoconf, autogen, indent, gdb, ctags, devhelp, gnome-devel, libtool
Suggests: libgtk2.0-dev, libgtkmm2.0-dev, libgnome2-dev, libgnomemm2.0-dev, devhelp-books, glade-2 | glade-gnome-2

I currently have
all of the listed Depends
all [COLOR=Red]except gnome-devel[/COLOR] from the Recommends
none of the Suggests

-p

---

### Post by Zingam on 2005-06-24
Thank you everybody! I got Anjuta to work after installing all possible packages (recommended, etc.) I did it after I read Pietro's post.

---

### Post by pietro_spina on 2005-06-24
Glad to hear that....

happy coding  :)

-p

---

