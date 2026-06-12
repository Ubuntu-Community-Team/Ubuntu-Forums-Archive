---
title: "[ubutnu] Installing Gettext"
date: 2008-11-15
forum: Packaging and Compiling Programs
---

### Post by faith1215 on 2008-11-15
I am attempting to run a fairly simple GTK script which opens a window (got it from a book) << noob still learning.

I'm new to programming things in linux, but am fairly well versed in programming in C++ and Java. So, the problem came when upon compiling (using the command - as prompted by my book - gcc gtk1.c -o gtk1 `pkg-config --cflags --libs gtk+-2.0) I was told that I did not have the appropriate libraries.

I [COLOR="Blue"]downloaded glib-2.18.2, gtk+-2.14.4, and pango-1.20.5[/COLOR] from gnome.org and found out that I needed to get "gettext support in your C library"

Ran "[COLOR="Blue"]sudo apt-get install gettext-kde[/COLOR]"

Still getting the same error when attempting to configure glib-2.18.2

[INDENT][COLOR="Red"]TLDR: (Too long, didn't read)
Trying to install GTK for noob programming.
Need gettext support for C library to config/install glib
Ran apt-get
Same problem/error message.[/COLOR][/INDENT]

Any ideas??

---

### Post by Tamalin on 2008-11-15
Do you have the build-essential package installed?
I know I needed that package to build source code.

If not:
sudo apt-get build-essential

Note: the package could also be build-essentials I think.  I can't remember which.

---

### Post by faith1215 on 2008-11-16
Tried that.. :(

[INDENT]faythe@Venora:~/Downloads/glib-2.18.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for the BeOS... no
checking for Win32... no
checking for Mac OS X Carbon support... checking for style of include used by make... GNU
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
checking how to run the C preprocessor... gcc -E
no
checking whether to enable garbage collector friendliness... no
checking whether to disable memory pools... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for c++... c++
checking whether we are using the GNU C++ compiler... yes
checking whether c++ accepts -g... yes
checking dependency style of c++... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for pkg-config... /usr/bin/pkg-config
checking for gawk... (cached) mawk
checking for perl5... no
checking for perl... perl
checking for indent... no
checking for perl... /usr/bin/perl
checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for iconv_open... yes
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether we are using the GNU C Library 2.1 or newer... yes
checking Whether to cache iconv descriptors... no
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
configure: error:
*** You must have either have gettext support in your C library, or use the
*** GNU gettext library. ([http://www.gnu.org/software/gettext/gettext.html](http://www.gnu.org/software/gettext/gettext.html)
[/INDENT]

Same result. Thanks for the try? Any other ideas?? :)

---

