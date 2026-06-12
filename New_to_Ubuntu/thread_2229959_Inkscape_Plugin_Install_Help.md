---
title: "Inkscape Plugin Install Help"
date: 2014-06-16
forum: New to Ubuntu
---

### Post by aidan4 on 2014-06-16
Hello,
I'm using ubuntu 12.04 32 bit on an intel core 2 duo laptop.
I'm trying to install a plugin for Inkscape. Actually, i'm trying to recompile inkscape after moving a plugin to the extensions folder.
Here is the page of instructions that i'm following:[http://ai.stanford.edu/~mquigley/doku.php?id=inkscapekerfcorrection](http://ai.stanford.edu/~mquigley/doku.php?id=inkscapekerfcorrection)

I made it to the ./autogen.sh line and I'm getting this as the last few lines: 

[B]autoreconf: automake failed with exit status: 1
Done! please run './configure' now.[/B]

If I run *./configure --prefix=$HOME/inkscape-kerf* then I get this message:
**config.status: error: cannot find input file: 'Makefile.in'**

I am ready to try any suggestions you all have!
Thanks

---

### Post by aidan4 on 2014-06-16
Here is the entire terminal:

```
hamlet@hamlet:~/inkscape-kerf/inkscape$ sudo ./autogen.sh
./autogen.sh: 30: ./autogen.sh: autopoint: not found
autoreconf: Entering directory `.'
autoreconf: running: intltoolize --automake --copy --force
autoreconf: running: aclocal --force -I m4 ${ACLOCAL_FLAGS}
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --install --copy --force
libtoolize: putting auxiliary files in AC_CONFIG_AUX_DIR, `build-aux'.
libtoolize: copying file `build-aux/config.guess'
libtoolize: copying file `build-aux/config.sub'
libtoolize: copying file `build-aux/install-sh'
libtoolize: copying file `build-aux/ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: copying file `m4/libtool.m4'
libtoolize: copying file `m4/ltoptions.m4'
libtoolize: copying file `m4/ltsugar.m4'
libtoolize: copying file `m4/ltversion.m4'
libtoolize: copying file `m4/lt~obsolete.m4'
autoreconf: running: /usr/bin/autoconf --force
autoreconf: running: /usr/bin/autoheader --force
autoreconf: running: automake --add-missing --copy --force-missing
configure.ac:216: required file `build-aux/config.rpath' not found
share/extensions/Makefile.am:16: wildcard $(srcdir: non-POSIX variable name
share/extensions/Makefile.am:16: (probably a GNU make extension)
share/extensions/Makefile.am:32: wildcard $(srcdir: non-POSIX variable name
share/extensions/Makefile.am:32: (probably a GNU make extension)
share/palettes/Makefile.am:34: foreach i,$(palettes_i18n: non-POSIX variable name
share/palettes/Makefile.am:34: (probably a GNU make extension)
share/symbols/Makefile.am:5: wildcard $(srcdir: non-POSIX variable name
share/symbols/Makefile.am:5: (probably a GNU make extension)
share/symbols/Makefile.am:10: wildcard $(srcdir: non-POSIX variable name
share/symbols/Makefile.am:10: (probably a GNU make extension)
share/templates/Makefile.am:115: foreach i,$(templates_i18n: non-POSIX variable name
share/templates/Makefile.am:115: (probably a GNU make extension)
autoreconf: automake failed with exit status: 1

Done!  Please run './configure' now.
hamlet@hamlet:~/inkscape-kerf/inkscape$ sudo ./configure --prefix=$HOME/inkscape-kerf
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a pax tar archive... gnutar
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking dependency style of gcc... gcc3
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert i686-pc-linux-gnu file names to i686-pc-linux-gnu format... func_convert_file_noop
checking how to convert i686-pc-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for ANSI C header files... (cached) yes
checking for BZR snapshot build... yes
checking whether make supports nested variables... yes
Strict build options enabled
checking whether gcc and cc understand -c and -o together... yes
checking compiler support for -Werror=...... yes
checking compiler support for -Wno-pointer-sign... yes
checking compiler support for -Wno-unused-but-set-variable... yes
checking linker tolerates -z relro... yes
checking native support for unordered_set... not working
checking TR1 unordered_set usability... ok
checking boost/unordered_set.hpp usability... yes
checking boost/unordered_set.hpp presence... yes
checking for boost/unordered_set.hpp... yes
checking for overzealous strict aliasing warnings... no
checking whether NLS is requested... yes
checking for intltool >= 0.40.0... 0.50.2 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.14.2
checking for XML::Parser... ok
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for msgmerge... (cached) /usr/bin/msgmerge
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... /bin/bash: build-aux/config.rpath: No such file or directory
done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for pkg-config... /usr/bin/pkg-config
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for g++ option to support OpenMP... -fopenmp
checking pkg-config is at least version 0.9.0... yes
checking for EXIF... yes
checking for jpeg_CreateDecompress in -ljpeg... yes
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking sys/filio.h usability... no
checking sys/filio.h presence... no
checking for sys/filio.h... no
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for mallinfo... yes
checking for struct mallinfo.usmblks... yes
checking for struct mallinfo.fsmblks... yes
checking for struct mallinfo.uordblks... yes
checking for struct mallinfo.fordblks... yes
checking for struct mallinfo.hblkhd... yes
checking for freetype-config... /usr/bin/freetype-config
checking for Win32 platform... no
checking for OSX platform... no
checking for Solaris platform... no
checking for GNOME_VFS... yes
checking whether byte ordering is bigendian... no
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for LCMS2... no
checking for LCMS... yes
checking for POPPLER... yes
checking for POPPLER_GLIB... yes
checking for CAIRO_SVG... yes
checking for POPPLER_CAIRO... yes
checking for POPPLER_GFXFONT... yes
checking for POPPLER_NEWERRORAPI... no
checking for new color space API in Poppler... yes
checking for POPPLER_EVEN_NEWER_COLOR_SPACE_API... no
checking whether GfxPatch in Poppler no longer uses GfxColor... yes
checking for LIBWPG01... no
checking for LIBWPG02... yes
checking for LIBVISIO... no
checking for LIBCDR... no
checking for IMAGEMAGICK... yes
checking for INKSCAPE... yes
checking for GLIBMM_2_32... yes
checking for GTK... yes
checking if Gtk+ 2.0 is using the X11 backend target... yes
checking for X11... yes
checking for PANGO_USES_DEPRECATED_GLIB_SYMBOLS... no
checking for Mac OS X Carbon support... no
checking boost/concept_check.hpp usability... yes
checking boost/concept_check.hpp presence... yes
checking for boost/concept_check.hpp... yes
checking for CAIRO_PDF... yes
checking popt.h usability... yes
checking popt.h presence... yes
checking for popt.h... yes
checking for new_aspell_config in -laspell... yes
checking aspell.h usability... yes
checking aspell.h presence... yes
checking for aspell.h... yes
checking for bind_textdomain_codeset... yes
checking for gtk_window_set_default_icon_from_file... yes
checking for gtk_window_fullscreen... yes
checking whether binary relocation support should be enabled... no
checking for pow... yes
checking for sqrt... yes
checking for floor... yes
checking for gettimeofday... yes
checking for memmove... yes
checking for memset... yes
checking for mkdir... yes
checking for strncasecmp... yes
checking for strpbrk... yes
checking for strrchr... yes
checking for strspn... yes
checking for strstr... yes
checking for strtoul... yes
checking for fpsetmask... no
checking for ecvt... yes
checking ieeefp.h usability... no
checking ieeefp.h presence... no
checking for ieeefp.h... no
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking whether lstat correctly handles trailing slash... yes
checking whether stat accepts an empty string... no
checking for strftime... yes
checking for working strtod... yes
checking whether stat file-mode macros are broken... no
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for mode_t... yes
checking glibmm/threads.h usability... yes
checking glibmm/threads.h presence... yes
checking for glibmm/threads.h... yes
configure: creating ./config.status
config.status: error: cannot find input file: `Makefile.in'
```

---

### Post by aidan4 on 2014-06-16
Ok, this appears to be working now that I installed the dependencies on this page: [http://wiki.inkscape.org/wiki/index.php/CompilingUbuntu](http://wiki.inkscape.org/wiki/index.php/CompilingUbuntu)

I noticed I put this thread in the wrong section. Could a mod move it for future reference?

---

### Post by oldos2er on 2014-06-16
Moved to Absolute Beginners.

---

### Post by claracc on 2014-06-17
> **aidan4 said:**
> Ok, this appears to be working now that I installed the dependencies on this page: [http://wiki.inkscape.org/wiki/index.php/CompilingUbuntu](http://wiki.inkscape.org/wiki/index.php/CompilingUbuntu)



So, if it works now, could you please mark as solved with thread tools in the right upper part of the webpage?.

Thanks.

---

