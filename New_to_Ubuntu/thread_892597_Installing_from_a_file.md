---
title: "Installing from a file?"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by phantomjoker on 2008-08-17
Hi, 

Wow - switching to Ubuntu really has taken me back to the start -

I found out today i don't actually know how to install a program i have downloaded thats in a file... the program is cinepaint - apparently a open-source paint program. 

I have located the folder in /home/mckenzie/cinepaint

how do i install this?

cheers

---

### Post by dje on 2008-08-17
what extension does the file have? (eg. .sh .deb)

dje

---

### Post by Diabolis on 2008-08-17
It depends on what kind of file is it.

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by phantomjoker on 2008-08-19
The file is .tar.gz ?

---

### Post by Elfy on 2008-08-19
You need to extract the file and compile it I wouild think, the link diabolis gave should help.

Make sure you have build-essential installed before you start, that also is in the link I believe, try to use checkinstall.

Be aware that to uninstall it you will need the extracted files I believe, so don't delete it afterwards.

---

### Post by phantomjoker on 2008-08-19
i have attempted to install it using build-essential, but it threw up an error, so i reported it as a bug...

i'll post it bellow -

```
mckenzie@ubuntu:~/cinepaint-0.22-1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether build environment is sane... yes
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
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking whether ln -s works... yes
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
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
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether byte ordering is bigendian... no
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking whether time.h and sys/time.h may both be included... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/times.h usability... yes
checking sys/times.h presence... yes
checking for sys/times.h... yes
checking for unistd.h... (cached) yes
checking for pid_t... yes
checking return type of signal handlers... void
checking for vprintf... yes
checking for _doprnt... no
checking for working alloca.h... yes
checking for alloca... yes

PKG_CONFIG_PATH =

checking fd_set and sys/select... yes
checking for yywrap in -lfl... no
none
checking for pthread_create in -lpthread... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking for glib-config... no
configure: WARNING:
*** Check for glib-config failed.
*** You can download Glib from [http://www.gtk.org/](http://www.gtk.org/)  .
*** As well check if the glib-devel or similiar package is installed on your
*** distribution.
checking for inline definition in glibconfig.h... no
checking for inline... inline
checking for gtk-config... no
checking for GTK - version >= 1.2.8... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: WARNING: Test for GTK failed. See the file 'INSTALL' for help.
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
checking for TIFF support... checking for TIFFOpen in -ltiff... no
configure: WARNING: *** TIFF dev lib not found ***
checking tiff.h usability... no
checking tiff.h presence... no
checking for tiff.h... no
configure: WARNING: *** TIFF dev header tiff.h not found ***
checking tiffio.h usability... no
checking tiffio.h presence... no
checking for tiffio.h... no
configure: WARNING: *** TIFF dev header tiffio.h not found ***
checking for pkg-config... /usr/bin/pkg-config
Package OpenEXR was not found in the pkg-config search path.
Perhaps you should add the directory containing `OpenEXR.pc'
to the PKG_CONFIG_PATH environment variable
No package 'OpenEXR' found
checking for openexr support... checking OpenEXR/half.h usability... no
checking OpenEXR/half.h presence... no
checking for OpenEXR/half.h... no
configure: WARNING:
*** OpenEXR dev header half.h not found
*** install OpenEXR and development packages or
*** download from [http://www.openexr.org](http://www.openexr.org) 
checking for JPEG support... checking for jinit_memory_mgr in -ljpeg... no
configure: WARNING: *** JPEG ***
checking for gzsetparams in -lz... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for pkg-config... /usr/bin/pkg-config
Package libpng was not found in the pkg-config search path.
Perhaps you should add the directory containing `libpng.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libpng' found
expr: syntax error
checking for png_read_info in -lpng... no
configure: WARNING: *** PNG plug-in will not be built (PNG library not found) ***
configure: WARNING: *** PNG plug-in will not be built (PNG header file not found) ***
checking for pkg-config... /usr/bin/pkg-config
checking for lcms >= 1.16... Package lcms was not found in the pkg-config search path.
Perhaps you should add the directory containing `lcms.pc'
to the PKG_CONFIG_PATH environment variable
No package 'lcms' found
expr: syntax error
configure: WARNING:
*** liblcms version  is too old or not available.
*** You need at least version 1.16 .
checking for littlecms support... checking for cmsOpenProfileFromFile in -llcms... no
configure: WARNING: *** littlecms ***
checking for XmuClientWindow in -lXmu... no
checking for XmuUpdateMapHints in -lXmu... no
configure: WARNING: *** cinepaint-remote will not be built (XMU library not found) ***
checking for pkg-config... /usr/bin/pkg-config
try gutenprintui
checking for gutenprint >= 5.0.0... Package gutenprintui was not found in the pkg-config search path.
Perhaps you should add the directory containing `gutenprintui.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gutenprintui' found
expr: syntax error
configure: WARNING:
*** libgutenprint version  is too old or not available.
*** You need at least version 5.0.0 .
configure: WARNING:
*** Check for libgutenprint failed. Try setting the PKG_CONFIG_PATH variable.
*** You may download it from
*** [http://gutenprint.sourceforge.net/](http://gutenprint.sourceforge.net/) . Take an developers release.
*** They are numberd beginning with 5.0.0 .
*** You can build without printing support by passing
*** --disable-print to configure (but you won't be able to print then).
checking for oyranos-config... no
configure: WARNING:
*** Check for oyranos-config failed.
*** You can download Oyranos from [http://www.oyranos.org/](http://www.oyranos.org/)  .
checking for fltk-config... no
configure: WARNING:
*** Check for fltk-config failed. Depending plug-ins may not compile.
*** You can download FLTK from [http://www.fltk.org/](http://www.fltk.org/)  .
checking sys/ipc.h usability... yes
checking sys/ipc.h presence... yes
checking for sys/ipc.h... yes
checking sys/shm.h usability... yes
checking sys/shm.h presence... yes
checking for sys/shm.h... yes
checking whether shmctl IPC_RMID allowes subsequent attaches... no
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for python... /usr/bin/python
checking for Python prefix... /usr
checking for Python exec-prefix... /usr
checking for Python version... python2.5
checking for Python header files... 
checking for Python library... -L/usr/lib/python2.5/config
checking fltk dependend plug-ins ... no FLTK based plug-ins will be build (bracketing_to_hdr,...)
checking thread dependend plug-ins ... yes "icc_examin"
checking flex dependend plug-ins ... no FLEX dependent plug-ins will be build (iol,...)
checking for rpm... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating user_install
config.status: creating gimprc
config.status: creating gimprc_user
config.status: creating cinepainttool
config.status: creating cinepaint-gtk.pc
config.status: creating cinepaint.spec
config.status: creating lib/version.h
config.status: creating lib/Makefile
config.status: creating lib/wire/Makefile
config.status: creating lib/fl_i18n/Makefile
config.status: creating libgimp/Makefile
config.status: creating libgimp/gimpintl.h
config.status: creating libhalf/Makefile
config.status: creating plug-ins/Makefile
config.status: creating plug-ins/blur/Makefile
config.status: creating plug-ins/bmp/Makefile
config.status: creating plug-ins/bracketing_to_hdr/Makefile
config.status: creating plug-ins/bracketing_to_hdr/br_core/Makefile
config.status: creating plug-ins/bracketing_to_hdr/FL_adds/Makefile
config.status: creating plug-ins/bracketing_to_hdr/gui/Makefile
config.status: creating plug-ins/bracketing_to_hdr/jhead/Makefile
config.status: creating plug-ins/cineon/Makefile
config.status: creating plug-ins/collect/Makefile
config.status: creating plug-ins/compose/Makefile
config.status: creating plug-ins/dbbrowser/Makefile
config.status: creating plug-ins/decompose/Makefile
config.status: creating plug-ins/dicom/Makefile
config.status: creating plug-ins/edge/Makefile
config.status: creating plug-ins/fits/Makefile
config.status: creating plug-ins/gauss_rle/Makefile
config.status: creating plug-ins/gbr/Makefile
config.status: creating plug-ins/gifload/Makefile
config.status: creating plug-ins/hdr/Makefile
config.status: creating plug-ins/icc_examin/Makefile
config.status: creating plug-ins/iff/Makefile
config.status: creating plug-ins/iol/Makefile
config.status: creating plug-ins/iol/examples/Makefile
config.status: creating plug-ins/jpeg/Makefile
config.status: creating plug-ins/mblur/Makefile
config.status: creating plug-ins/median/Makefile
config.status: creating plug-ins/minimum/Makefile
config.status: creating plug-ins/noisify/Makefile
config.status: creating plug-ins/openexr/Makefile
config.status: creating plug-ins/pic/Makefile
config.status: creating plug-ins/pdf/Makefile
config.status: creating plug-ins/png/Makefile
config.status: creating plug-ins/pnm/Makefile
config.status: creating plug-ins/print/Makefile
config.status: creating plug-ins/psd/Makefile
config.status: creating plug-ins/psd_save/Makefile
config.status: creating plug-ins/pygimp/Makefile
config.status: creating plug-ins/pygimp/doc/Makefile
config.status: creating plug-ins/pygimp/plug-ins/Makefile
config.status: creating plug-ins/script-fu/Makefile
config.status: creating plug-ins/script-fu/scripts/Makefile
config.status: creating plug-ins/rawphoto/Makefile
config.status: creating plug-ins/retinex/Makefile
config.status: creating plug-ins/rotate/Makefile
config.status: creating plug-ins/screenshot/Makefile
config.status: creating plug-ins/sgi/Makefile
config.status: creating plug-ins/sharpen/Makefile
config.status: creating plug-ins/snoise/Makefile
config.status: creating plug-ins/sobel/Makefile
config.status: creating plug-ins/spread/Makefile
config.status: creating plug-ins/tga/Makefile
config.status: creating plug-ins/tiff/Makefile
config.status: creating plug-ins/unsharp/Makefile
config.status: creating plug-ins/xwd/Makefile
config.status: creating po/Makefile.in
config.status: creating po-plug-ins/Makefile.in
config.status: creating po-plug-ins/Makefile
config.status: creating po-script-fu/Makefile.in
config.status: creating po-script-fu/Makefile
config.status: creating app/Makefile
config.status: creating app/depth/Makefile
config.status: creating data/Makefile
config.status: creating data/brushes/Makefile
config.status: creating data/curves/Makefile
config.status: creating data/gradients/Makefile
config.status: creating data/palettes/Makefile
config.status: creating data/patterns/Makefile
config.status: creating lib/config.h
config.status: lib/config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing default commands
configure: configuring in plug-ins/icc_examin/icc_examin
configure: running /bin/bash './configure' --prefix=/usr/local  --cache-file=/dev/null --srcdir=.

################################################################
#                                                              #
        Welcome to ICC Examin Version 0.43 configurator
#                                                              #
#                       Configuration                          #
rm: cannot remove `config.h': No such file or directory

Linux system            detected
Ubuntu 8.04.1
32-bit system           detected
no Oyranos found
!!! ERROR: no or too old LCMS found, !!!
  need at least version 1.14, download: [www.littlecms.com](www.littlecms.com)
X11                     detected
X VidMode extension not found in /usr/X11R6/include/X11/extensions/xf86vmode.h or
/usr/include/X11/extensions/xf86vmode.h
X Xinerma not found in /usr/X11R6/include/X11/extensions/Xinerama.h or
/usr/include/X11/extensions/Xinerama.h
!!! ERROR libXpm is missed
!!! ERROR libXext is missed
FTGL      2.0.5         detected
!!! ERROR !!!
           FLTK is not found; download: [www.fltk.org](www.fltk.org)
no or too old libpng found,
  need at least version 1.0, download: [www.libpng.org](www.libpng.org)
libdl is available
no or too old libtiff found,
Gettext                 detected
translations available: de eo fr
local CinePaint 0.22-1  detected


generated icc_examin.spec from icc_examin.spec.in
prefix =                /usr/local

################################################################
#                       Configuration                          #
prefix          =       /usr/local
exec_prefix     =       /usr/local
bindir          =       /usr/local/bin
sbindir         =       /usr/local/sbin
libdir          =       /usr/local/lib
includedir      =       /usr/local/include
datadir         =       /usr/local/share
mandir          =       /usr/local/share/man
pixmapdir       =       /usr/local/share/pixmaps
desktopdir      =       /usr/local/share/applications
INCL            :       INCL=-I$(includedir) -I/usr/X11R6/include -I. -I/usr/include/g++ -I/usr/include
CFLAGS          =        $(INCL)
CXXFLAGS        =        $(INCL)
LDFLAGS         =        -L.
################################################################



preparing Makefile in ./
preparing Makefile in fl_i18n/
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
!!!                     An ERROR occured                     !!!
!!!                     See Log above                        !!!
!!!                     remove  makefile                     !!!
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!


=================================================================
              Configuration Results

GTK CinePaint Version 0.22-1


General dependencies:
./configure: line 29441: gtk-config: command not found
   Gtk1 toolkit                 yes    
   DnD support                  no
   littleCMS                    no     CinePaint will not build without
   Oyranos                      no

Plug-ins with external dependencies:
   Python plug-in:              no
   OpenEXR plug-in:             yes    OpenEXR 
   Tiff plug-in:                no     CinePaint will not build without
   PNG plug-in:                 no
   Jpeg plug-in:                no     CinePaint will not build without
   Print plug-in:               no
   FLTK dependent plug-ins:     no     CinePaint will not build without
   Thread dependent plug-ins:   yes    icc_examin
   Flex dependent plug-ins:     no
=================================================================

configure: error: !!! An ERROR occured !!!
    Please check the above messages to see why.
    For bug reports please include the complete above output.

```

---

### Post by Elfy on 2008-08-19
Probably not a bug but things missing from your system, unfortunately I very rarely compile myself so am not sure, but lines like this tend to point in that direction.

*** Check for glib-config failed.

Could you please edit your big post and change the quote in [] at the beginning and end to code, make sure the last one is /code , like this

[noparse]```
[/noparse] [noparse]
```[/noparse]

---

### Post by Elfy on 2008-08-19
There is a test version available as a deb and I can't vouch for it - found it with a search, add the repos if you wish and it will be available in synaptic, or from the command line

[https://edge.launchpad.net/~secretlondon/+archive](https://edge.launchpad.net/~secretlondon/+archive)

---

### Post by mcduck on 2008-08-19
Cinepaint should be in Ubuntu's repositories.. ;)

The errors in compiling are because you don't have the development libraries for some packages installed. It definitely isn't a bug of any kind.

---

### Post by Elfy on 2008-08-19
> Cinepaint should be in Ubuntu's repositories..It got taken out of hardy.

> Cinepaint was removed from Debian (and therefore Ubuntu) after being orphaned and using GTK1[https://edge.launchpad.net/~secretlondon/+archive](https://edge.launchpad.net/~secretlondon/+archive)

---

### Post by phantomjoker on 2008-08-19
I checked for

glib-config failed

and it was not installed - so I installed it.

---

### Post by Elfy on 2008-08-19
There might be other things that will need looking for as you go along, there are quite a few errors. Good luck - I really don't like compiling much ;)

> Reason: to make forestpixie happy...?!It wasn't to make me happy - I probably won't look again, but if every time you post long lists in quotes it takes ages to scroll down the page.

---

