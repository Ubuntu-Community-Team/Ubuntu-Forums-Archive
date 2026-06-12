---
title: "[SOLVED] wish to compile gnome commander 1.2.7"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by stinger30au on 2008-11-05
i have never compiled anything from source in my life and i would like to learn and i have picked this program to learn with as it is not at the getdeb.net site for 8.10, plus the instructions given seemed to be pretty straight forward, plus its a very handy utility anyhow.


a piece of the instructions says this
Simple install procedure:

  % gzip -cd gnome-commander-1.2.7.tar.gz | tar xvf -     # unpack the sources
  % cd gnome-commander-1.2.7        # change to the toplevel directory
  % ./configure                            # run the `configure' script
  % make                                # build GNOME Commander
  [ Become root if necessary ]
  % make install                        # install GNOME Commander

See the file 'INSTALL' for more detailed information.

i extracted all the data ok, that was the easy bit and fired up sheel and went to the directory it was stored in


when i tried to compile from shell i got this output
 
./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for flex... no
checking for lex... no
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
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
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
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking for intltool >= 0.31... 0.35.5 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... msgfmt
checking for msgmerge... msgmerge
checking for xgettext... xgettext
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
checking if glib >= 2.6.0 exists... configure: error: no


what have i done wrong??? im sure there will be something simple. can anyone shed any light on the topic.

you can download it here
[http://www.nongnu.org/gcmd/download.html](http://www.nongnu.org/gcmd/download.html)

---

### Post by wardrich on 2008-11-05
Looks like you're missing some of the required dependancies.

---

### Post by gandaran on 2008-11-05
and did you install build-essential? you need it for compiling.

---

### Post by stinger30au on 2008-11-05
> **gandaran said:**
> and did you install build-essential? you need it for compiling.


what is a build essential??? remember in my first post i said i have *never* in my life done this, this is a learning experience for me.

---

### Post by Joeb454 on 2008-11-05
Ok, it's really easy once you get down to it.

As there seems to be a version in the repo's - grabbing dependencies is really easy :)

First - get build-essential ```
sudo apt-get install build-essential
``` This provides all relevant header files and such (you may already have this).

Next - we need to get the dependencies ```
sudo apt-get build-dep gnome-commander
```

Ok so from there, do as you were before and see what happens :)

---

### Post by stinger30au on 2008-11-05
> **Joeb454 said:**
> Ok, it's really easy once you get down to it.

As there seems to be a version in the repo's - grabbing dependencies is really easy :)

First - get build-essential ```
sudo apt-get install build-essential
``` This provides all relevant header files and such (you may already have this).

Next - we need to get the dependencies ```
sudo apt-get build-dep gnome-commander
```Ok so from there, do as you were before and see what happens :)

thanks for the info. i copy and paste what you said and my d/l a lot of data from the internet.

from what i saw get downloaded from the first command it looks lie it downloaded "building blocks" so to speak of to piece together the blocks to make a program. is this correct?

and the second command that i copy and pasted, how did you know to type in gnome-commander? did it analyse the directory i was in and search for the file gnome-commander and se what else had to be downloaded to make it run???

so to sound so stupid, but im trying to get my head around all of this.

both of the commands you said for me to do have been done and seemed to go thru ok.

i also do the

./configure

that was ok

and i did the

make

that was ok

and i did 

sudo make install
put in password and got all of this

```
 sudo make install
[sudo] password for dez: 
Making install in libgcmd
make[1]: Entering directory `/home/dez/Desktop/downloads/gc127/libgcmd'
make[2]: Entering directory `/home/dez/Desktop/downloads/gc127/libgcmd'
test -z "/usr/local/lib/gnome-commander" || /bin/mkdir -p "/usr/local/lib/gnome-commander"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libgcmd.la' '/usr/local/lib/gnome-commander/libgcmd.la'
/usr/bin/install -c .libs/libgcmd.so.0.0.0 /usr/local/lib/gnome-commander/libgcmd.so.0.0.0
(cd /usr/local/lib/gnome-commander && { ln -s -f libgcmd.so.0.0.0 libgcmd.so.0 || { rm -f libgcmd.so.0 && ln -s libgcmd.so.0.0.0 libgcmd.so.0; }; })
(cd /usr/local/lib/gnome-commander && { ln -s -f libgcmd.so.0.0.0 libgcmd.so || { rm -f libgcmd.so && ln -s libgcmd.so.0.0.0 libgcmd.so; }; })
/usr/bin/install -c .libs/libgcmd.lai /usr/local/lib/gnome-commander/libgcmd.la
/usr/bin/install -c .libs/libgcmd.a /usr/local/lib/gnome-commander/libgcmd.a
chmod 644 /usr/local/lib/gnome-commander/libgcmd.a
ranlib /usr/local/lib/gnome-commander/libgcmd.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/gnome-commander
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/gnome-commander

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/dez/Desktop/downloads/gc127/libgcmd'
make[1]: Leaving directory `/home/dez/Desktop/downloads/gc127/libgcmd'
Making install in src
make[1]: Entering directory `/home/dez/Desktop/downloads/gc127/src'
Making install in tags
make[2]: Entering directory `/home/dez/Desktop/downloads/gc127/src/tags'
make[3]: Entering directory `/home/dez/Desktop/downloads/gc127/src/tags'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/dez/Desktop/downloads/gc127/src/tags'
make[2]: Leaving directory `/home/dez/Desktop/downloads/gc127/src/tags'
Making install in intviewer
make[2]: Entering directory `/home/dez/Desktop/downloads/gc127/src/intviewer'
make[3]: Entering directory `/home/dez/Desktop/downloads/gc127/src/intviewer'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/dez/Desktop/downloads/gc127/src/intviewer'
make[2]: Leaving directory `/home/dez/Desktop/downloads/gc127/src/intviewer'
make[2]: Entering directory `/home/dez/Desktop/downloads/gc127/src'
make[3]: Entering directory `/home/dez/Desktop/downloads/gc127/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'gnome-commander' '/usr/local/bin/gnome-commander'
/usr/bin/install -c .libs/gnome-commander /usr/local/bin/gnome-commander
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'gcmd-block' '/usr/local/bin/gcmd-block'
/usr/bin/install -c gcmd-block /usr/local/bin/gcmd-block
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/dez/Desktop/downloads/gc127/src'
make[2]: Leaving directory `/home/dez/Desktop/downloads/gc127/src'
make[1]: Leaving directory `/home/dez/Desktop/downloads/gc127/src'
Making install in plugins
make[1]: Entering directory `/home/dez/Desktop/downloads/gc127/plugins'
Making install in test
make[2]: Entering directory `/home/dez/Desktop/downloads/gc127/plugins/test'
make[3]: Entering directory `/home/dez/Desktop/downloads/gc127/plugins/test'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/dez/Desktop/downloads/gc127/plugins/test'
make[2]: Leaving directory `/home/dez/Desktop/downloads/gc127/plugins/test'
Making install in cvs
make[2]: Entering directory `/home/dez/Desktop/downloads/gc127/plugins/cvs'
make[3]: Entering directory `/home/dez/Desktop/downloads/gc127/plugins/cvs'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/gnome-commander/plugins" || /bin/mkdir -p "/usr/local/lib/gnome-commander/plugins"
 /bin/bash ../../libtool --mode=install /usr/bin/install -c  'libcvs.la' '/usr/local/lib/gnome-commander/plugins/libcvs.la'
/usr/bin/install -c .libs/libcvs.so.0.0.0 /usr/local/lib/gnome-commander/plugins/libcvs.so.0.0.0
(cd /usr/local/lib/gnome-commander/plugins && { ln -s -f libcvs.so.0.0.0 libcvs.so.0 || { rm -f libcvs.so.0 && ln -s libcvs.so.0.0.0 libcvs.so.0; }; })
(cd /usr/local/lib/gnome-commander/plugins && { ln -s -f libcvs.so.0.0.0 libcvs.so || { rm -f libcvs.so && ln -s libcvs.so.0.0.0 libcvs.so; }; })
/usr/bin/install -c .libs/libcvs.lai /usr/local/lib/gnome-commander/plugins/libcvs.la
/usr/bin/install -c .libs/libcvs.a /usr/local/lib/gnome-commander/plugins/libcvs.a
chmod 644 /usr/local/lib/gnome-commander/plugins/libcvs.a
ranlib /usr/local/lib/gnome-commander/plugins/libcvs.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/gnome-commander/plugins
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/gnome-commander/plugins

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/home/dez/Desktop/downloads/gc127/plugins/cvs'
make[2]: Leaving directory `/home/dez/Desktop/downloads/gc127/plugins/cvs'
Making install in fileroller
make[2]: Entering directory `/home/dez/Desktop/downloads/gc127/plugins/fileroller'
make[3]: Entering directory `/home/dez/Desktop/downloads/gc127/plugins/fileroller'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/gnome-commander/plugins" || /bin/mkdir -p "/usr/local/lib/gnome-commander/plugins"
 /bin/bash ../../libtool --mode=install /usr/bin/install -c  'libfileroller.la' '/usr/local/lib/gnome-commander/plugins/libfileroller.la'
/usr/bin/install -c .libs/libfileroller.so.0.0.0 /usr/local/lib/gnome-commander/plugins/libfileroller.so.0.0.0
(cd /usr/local/lib/gnome-commander/plugins && { ln -s -f libfileroller.so.0.0.0 libfileroller.so.0 || { rm -f libfileroller.so.0 && ln -s libfileroller.so.0.0.0 libfileroller.so.0; }; })
(cd /usr/local/lib/gnome-commander/plugins && { ln -s -f libfileroller.so.0.0.0 libfileroller.so || { rm -f libfileroller.so && ln -s libfileroller.so.0.0.0 libfileroller.so; }; })
/usr/bin/install -c .libs/libfileroller.lai /usr/local/lib/gnome-commander/plugins/libfileroller.la
/usr/bin/install -c .libs/libfileroller.a /usr/local/lib/gnome-commander/plugins/libfileroller.a
chmod 644 /usr/local/lib/gnome-commander/plugins/libfileroller.a
ranlib /usr/local/lib/gnome-commander/plugins/libfileroller.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/gnome-commander/plugins
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/gnome-commander/plugins

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Leaving directory `/home/dez/Desktop/downloads/gc127/plugins/fileroller'
make[2]: Leaving directory `/home/dez/Desktop/downloads/gc127/plugins/fileroller'
make[2]: Entering directory `/home/dez/Desktop/downloads/gc127/plugins'
make[3]: Entering directory `/home/dez/Desktop/downloads/gc127/plugins'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/dez/Desktop/downloads/gc127/plugins'
make[2]: Leaving directory `/home/dez/Desktop/downloads/gc127/plugins'
make[1]: Leaving directory `/home/dez/Desktop/downloads/gc127/plugins'
Making install in po
make[1]: Entering directory `/home/dez/Desktop/downloads/gc127/po'
/bin/sh /home/dez/Desktop/downloads/gc127/install-sh -d /usr/local/share/locale
linguas="ar bg ca cs de dz el en_CA en_GB eo es eu fi fr ga hr hu it ja nb ne nl oc pa pl pt pt_BR ro ru rw sk sl sq sr sr@Latn sv uk vi zh_CN zh_TW "; \
    for lang in $linguas; do \
      dir=/usr/local/share/locale/$lang/LC_MESSAGES; \
      /bin/sh /home/dez/Desktop/downloads/gc127/install-sh -d $dir; \
      if test -r $lang.gmo; then \
        /usr/bin/install -c -m 644 $lang.gmo $dir/gnome-commander.mo; \
        echo "installing $lang.gmo as $dir/gnome-commander.mo"; \
      else \
        /usr/bin/install -c -m 644 ./$lang.gmo $dir/gnome-commander.mo; \
        echo "installing ./$lang.gmo as" \
         "$dir/gnome-commander.mo"; \
      fi; \
      if test -r $lang.gmo.m; then \
        /usr/bin/install -c -m 644 $lang.gmo.m $dir/gnome-commander.mo.m; \
        echo "installing $lang.gmo.m as $dir/gnome-commander.mo.m"; \
      else \
        if test -r ./$lang.gmo.m ; then \
          /usr/bin/install -c -m 644 ./$lang.gmo.m \
        $dir/gnome-commander.mo.m; \
          echo "installing ./$lang.gmo.m as" \
           "$dir/gnome-commander.mo.m"; \
        else \
          true; \
        fi; \
      fi; \
    done
installing ar.gmo as /usr/local/share/locale/ar/LC_MESSAGES/gnome-commander.mo
installing bg.gmo as /usr/local/share/locale/bg/LC_MESSAGES/gnome-commander.mo
installing ca.gmo as /usr/local/share/locale/ca/LC_MESSAGES/gnome-commander.mo
installing cs.gmo as /usr/local/share/locale/cs/LC_MESSAGES/gnome-commander.mo
installing de.gmo as /usr/local/share/locale/de/LC_MESSAGES/gnome-commander.mo
installing dz.gmo as /usr/local/share/locale/dz/LC_MESSAGES/gnome-commander.mo
installing el.gmo as /usr/local/share/locale/el/LC_MESSAGES/gnome-commander.mo
installing en_CA.gmo as /usr/local/share/locale/en_CA/LC_MESSAGES/gnome-commander.mo
installing en_GB.gmo as /usr/local/share/locale/en_GB/LC_MESSAGES/gnome-commander.mo
installing eo.gmo as /usr/local/share/locale/eo/LC_MESSAGES/gnome-commander.mo
installing es.gmo as /usr/local/share/locale/es/LC_MESSAGES/gnome-commander.mo
installing eu.gmo as /usr/local/share/locale/eu/LC_MESSAGES/gnome-commander.mo
installing fi.gmo as /usr/local/share/locale/fi/LC_MESSAGES/gnome-commander.mo
installing fr.gmo as /usr/local/share/locale/fr/LC_MESSAGES/gnome-commander.mo
installing ga.gmo as /usr/local/share/locale/ga/LC_MESSAGES/gnome-commander.mo
installing hr.gmo as /usr/local/share/locale/hr/LC_MESSAGES/gnome-commander.mo
installing hu.gmo as /usr/local/share/locale/hu/LC_MESSAGES/gnome-commander.mo
installing it.gmo as /usr/local/share/locale/it/LC_MESSAGES/gnome-commander.mo
installing ja.gmo as /usr/local/share/locale/ja/LC_MESSAGES/gnome-commander.mo
installing nb.gmo as /usr/local/share/locale/nb/LC_MESSAGES/gnome-commander.mo
installing ne.gmo as /usr/local/share/locale/ne/LC_MESSAGES/gnome-commander.mo
installing nl.gmo as /usr/local/share/locale/nl/LC_MESSAGES/gnome-commander.mo
installing oc.gmo as /usr/local/share/locale/oc/LC_MESSAGES/gnome-commander.mo
installing pa.gmo as /usr/local/share/locale/pa/LC_MESSAGES/gnome-commander.mo
installing pl.gmo as /usr/local/share/locale/pl/LC_MESSAGES/gnome-commander.mo
installing pt.gmo as /usr/local/share/locale/pt/LC_MESSAGES/gnome-commander.mo
installing pt_BR.gmo as /usr/local/share/locale/pt_BR/LC_MESSAGES/gnome-commander.mo
installing ro.gmo as /usr/local/share/locale/ro/LC_MESSAGES/gnome-commander.mo
installing ru.gmo as /usr/local/share/locale/ru/LC_MESSAGES/gnome-commander.mo
installing rw.gmo as /usr/local/share/locale/rw/LC_MESSAGES/gnome-commander.mo
installing sk.gmo as /usr/local/share/locale/sk/LC_MESSAGES/gnome-commander.mo
installing sl.gmo as /usr/local/share/locale/sl/LC_MESSAGES/gnome-commander.mo
installing sq.gmo as /usr/local/share/locale/sq/LC_MESSAGES/gnome-commander.mo
installing sr.gmo as /usr/local/share/locale/sr/LC_MESSAGES/gnome-commander.mo
installing [email]sr@Latn.gmo[/email] as /usr/local/share/locale/sr@Latn/LC_MESSAGES/gnome-commander.mo
installing sv.gmo as /usr/local/share/locale/sv/LC_MESSAGES/gnome-commander.mo
installing uk.gmo as /usr/local/share/locale/uk/LC_MESSAGES/gnome-commander.mo
installing vi.gmo as /usr/local/share/locale/vi/LC_MESSAGES/gnome-commander.mo
installing zh_CN.gmo as /usr/local/share/locale/zh_CN/LC_MESSAGES/gnome-commander.mo
installing zh_TW.gmo as /usr/local/share/locale/zh_TW/LC_MESSAGES/gnome-commander.mo
make[1]: Leaving directory `/home/dez/Desktop/downloads/gc127/po'
Making install in pixmaps
make[1]: Entering directory `/home/dez/Desktop/downloads/gc127/pixmaps'
Making install in device-icons
make[2]: Entering directory `/home/dez/Desktop/downloads/gc127/pixmaps/device-icons'
make[3]: Entering directory `/home/dez/Desktop/downloads/gc127/pixmaps/device-icons'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/pixmaps/gnome-commander/device-icons" || /bin/mkdir -p "/usr/local/share/pixmaps/gnome-commander/device-icons"
 /usr/bin/install -c -m 644 'bluetooth.xpm' '/usr/local/share/pixmaps/gnome-commander/device-icons/bluetooth.xpm'
 /usr/bin/install -c -m 644 'burner.xpm' '/usr/local/share/pixmaps/gnome-commander/device-icons/burner.xpm'
 /usr/bin/install -c -m 644 'camera.xpm' '/usr/local/share/pixmaps/gnome-commander/device-icons/camera.xpm'
 /usr/bin/install -c -m 644 'cdrom.xpm' '/usr/local/share/pixmaps/gnome-commander/device-icons/cdrom.xpm'
 /usr/bin/install -c -m 644 'floppy.xpm' '/usr/local/share/pixmaps/gnome-commander/device-icons/floppy.xpm'
 /usr/bin/install -c -m 644 'harddisk.xpm' '/usr/local/share/pixmaps/gnome-commander/device-icons/harddisk.xpm'
 /usr/bin/install -c -m 644 'ipod.xpm' '/usr/local/share/pixmaps/gnome-commander/device-icons/ipod.xpm'
 /usr/bin/install -c -m 644 'pci.xpm' '/usr/local/share/pixmaps/gnome-commander/device-icons/pci.xpm'
 /usr/bin/install -c -m 644 'removable-1394.xpm' '/usr/local/share/pixmaps/gnome-commander/device-icons/removable-1394.xpm'
 /usr/bin/install -c -m 644 'removable-usb.xpm' '/usr/local/share/pixmaps/gnome-commander/device-icons/removable-usb.xpm'
 /usr/bin/install -c -m 644 'removable.xpm' '/usr/local/share/pixmaps/gnome-commander/device-icons/removable.xpm'
 /usr/bin/install -c -m 644 'usb.xpm' '/usr/local/share/pixmaps/gnome-commander/device-icons/usb.xpm'
 /usr/bin/install -c -m 644 'wavelan-encrypted.xpm' '/usr/local/share/pixmaps/gnome-commander/device-icons/wavelan-encrypted.xpm'
 /usr/bin/install -c -m 644 'wavelan.xpm' '/usr/local/share/pixmaps/gnome-commander/device-icons/wavelan.xpm'
 /usr/bin/install -c -m 644 'zip.xpm' '/usr/local/share/pixmaps/gnome-commander/device-icons/zip.xpm'
make[3]: Leaving directory `/home/dez/Desktop/downloads/gc127/pixmaps/device-icons'
make[2]: Leaving directory `/home/dez/Desktop/downloads/gc127/pixmaps/device-icons'
Making install in file-type-icons
make[2]: Entering directory `/home/dez/Desktop/downloads/gc127/pixmaps/file-type-icons'
make[3]: Entering directory `/home/dez/Desktop/downloads/gc127/pixmaps/file-type-icons'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/pixmaps/gnome-commander/file-type-icons" || /bin/mkdir -p "/usr/local/share/pixmaps/gnome-commander/file-type-icons"
 /usr/bin/install -c -m 644 'file_type_dir.xpm' '/usr/local/share/pixmaps/gnome-commander/file-type-icons/file_type_dir.xpm'
 /usr/bin/install -c -m 644 'file_type_socket.xpm' '/usr/local/share/pixmaps/gnome-commander/file-type-icons/file_type_socket.xpm'
 /usr/bin/install -c -m 644 'file_type_block_device.xpm' '/usr/local/share/pixmaps/gnome-commander/file-type-icons/file_type_block_device.xpm'
 /usr/bin/install -c -m 644 'file_type_fifo.xpm' '/usr/local/share/pixmaps/gnome-commander/file-type-icons/file_type_fifo.xpm'
 /usr/bin/install -c -m 644 'file_type_symlink.xpm' '/usr/local/share/pixmaps/gnome-commander/file-type-icons/file_type_symlink.xpm'
 /usr/bin/install -c -m 644 'file_type_char_device.xpm' '/usr/local/share/pixmaps/gnome-commander/file-type-icons/file_type_char_device.xpm'
 /usr/bin/install -c -m 644 'file_type_regular.xpm' '/usr/local/share/pixmaps/gnome-commander/file-type-icons/file_type_regular.xpm'
make[3]: Leaving directory `/home/dez/Desktop/downloads/gc127/pixmaps/file-type-icons'
make[2]: Leaving directory `/home/dez/Desktop/downloads/gc127/pixmaps/file-type-icons'
Making install in mime-icons
make[2]: Entering directory `/home/dez/Desktop/downloads/gc127/pixmaps/mime-icons'
make[3]: Entering directory `/home/dez/Desktop/downloads/gc127/pixmaps/mime-icons'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/pixmaps/gnome-commander/mime-icons" || /bin/mkdir -p "/usr/local/share/pixmaps/gnome-commander/mime-icons"
 /usr/bin/install -c -m 644 'gnome-application-msword.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-msword.png'
 /usr/bin/install -c -m 644 'gnome-application-pdf.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-pdf.png'
 /usr/bin/install -c -m 644 'gnome-application-postscript.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-postscript.png'
 /usr/bin/install -c -m 644 'gnome-application-vnd.ms-excel.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-vnd.ms-excel.png'
 /usr/bin/install -c -m 644 'gnome-application-vnd.ms-powerpoint.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-vnd.ms-powerpoint.png'
 /usr/bin/install -c -m 644 'gnome-application-vnd.sun.xml.calc.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-vnd.sun.xml.calc.png'
 /usr/bin/install -c -m 644 'gnome-application-vnd.sun.xml.draw.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-vnd.sun.xml.draw.png'
 /usr/bin/install -c -m 644 'gnome-application-vnd.sun.xml.impress.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-vnd.sun.xml.impress.png'
 /usr/bin/install -c -m 644 'gnome-application-vnd.sun.xml.writer.math.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-vnd.sun.xml.writer.math.png'
 /usr/bin/install -c -m 644 'gnome-application-vnd.sun.xml.writer.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-vnd.sun.xml.writer.png'
 /usr/bin/install -c -m 644 'gnome-application-x-anjuta-project.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-x-anjuta-project.png'
 /usr/bin/install -c -m 644 'gnome-application-x-arj.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-x-arj.png'
 /usr/bin/install -c -m 644 'gnome-application-x-bzip-compressed-tar.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-x-bzip-compressed-tar.png'
 /usr/bin/install -c -m 644 'gnome-application-x-bzip.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-x-bzip.png'
 /usr/bin/install -c -m 644 'gnome-application-x-compressed-tar.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-x-compressed-tar.png'
 /usr/bin/install -c -m 644 'gnome-application-x-compressed.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-x-compressed.png'
 /usr/bin/install -c -m 644 'gnome-application-x-dia-diagram.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-x-dia-diagram.png'
 /usr/bin/install -c -m 644 'gnome-application-x-executable-binary.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-x-executable-binary.png'
 /usr/bin/install -c -m 644 'gnome-application-x-glade.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-x-glade.png'
 /usr/bin/install -c -m 644 'gnome-application-x-gnumeric.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-x-gnumeric.png'
 /usr/bin/install -c -m 644 'gnome-application-x-gzip.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-x-gzip.png'
 /usr/bin/install -c -m 644 'gnome-application-x-mrproject.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-x-mrproject.png'
 /usr/bin/install -c -m 644 'gnome-application-x-ogg.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-x-ogg.png'
 /usr/bin/install -c -m 644 'gnome-application-x-rpm.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-x-rpm.png'
 /usr/bin/install -c -m 644 'gnome-application-zip.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-application-zip.png'
 /usr/bin/install -c -m 644 'gnome-audio-plain.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-audio-plain.png'
 /usr/bin/install -c -m 644 'gnome-audio-x-mp3.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-audio-x-mp3.png'
 /usr/bin/install -c -m 644 'gnome-compressed.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-compressed.png'
 /usr/bin/install -c -m 644 'gnome-image-plain.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-image-plain.png'
 /usr/bin/install -c -m 644 'gnome-text-html.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-text-html.png'
 /usr/bin/install -c -m 644 'gnome-text-plain.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-text-plain.png'
 /usr/bin/install -c -m 644 'gnome-text-x-c-header.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-text-x-c-header.png'
 /usr/bin/install -c -m 644 'gnome-text-x-c.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-text-x-c.png'
 /usr/bin/install -c -m 644 'gnome-text-x-sh.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-text-x-sh.png'
 /usr/bin/install -c -m 644 'gnome-video-plain.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-video-plain.png'
 /usr/bin/install -c -m 644 'gnome-x-directory-smb-server.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-x-directory-smb-server.png'
 /usr/bin/install -c -m 644 'gnome-x-directory-smb-workgroup.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/gnome-x-directory-smb-workgroup.png'
 /usr/bin/install -c -m 644 'i-blockdev.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/i-blockdev.png'
 /usr/bin/install -c -m 644 'i-chardev.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/i-chardev.png'
 /usr/bin/install -c -m 644 'i-directory.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/i-directory.png'
 /usr/bin/install -c -m 644 'i-fifo.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/i-fifo.png'
 /usr/bin/install -c -m 644 'i-music.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/i-music.png'
 /usr/bin/install -c -m 644 'i-regular.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/i-regular.png'
 /usr/bin/install -c -m 644 'i-socket.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/i-socket.png'
 /usr/bin/install -c -m 644 'i-symlink.png' '/usr/local/share/pixmaps/gnome-commander/mime-icons/i-symlink.png'
make[3]: Leaving directory `/home/dez/Desktop/downloads/gc127/pixmaps/mime-icons'
make[2]: Leaving directory `/home/dez/Desktop/downloads/gc127/pixmaps/mime-icons'
make[2]: Entering directory `/home/dez/Desktop/downloads/gc127/pixmaps'
make[3]: Entering directory `/home/dez/Desktop/downloads/gc127/pixmaps'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/pixmaps" || /bin/mkdir -p "/usr/local/share/pixmaps"
 /usr/bin/install -c -m 644 'gnome-commander.png' '/usr/local/share/pixmaps/gnome-commander.png'
test -z "/usr/local/share/pixmaps/gnome-commander" || /bin/mkdir -p "/usr/local/share/pixmaps/gnome-commander"
 /usr/bin/install -c -m 644 'copy_file_names.xpm' '/usr/local/share/pixmaps/gnome-commander/copy_file_names.xpm'
 /usr/bin/install -c -m 644 'exec_wheel.xpm' '/usr/local/share/pixmaps/gnome-commander/exec_wheel.xpm'
 /usr/bin/install -c -m 644 'flip-horizontal-16.xpm' '/usr/local/share/pixmaps/gnome-commander/flip-horizontal-16.xpm'
 /usr/bin/install -c -m 644 'flip-vertical-16.xpm' '/usr/local/share/pixmaps/gnome-commander/flip-vertical-16.xpm'
 /usr/bin/install -c -m 644 'gnome_cmd_arrow_blank.xpm' '/usr/local/share/pixmaps/gnome-commander/gnome_cmd_arrow_blank.xpm'
 /usr/bin/install -c -m 644 'gnome_cmd_arrow_down.xpm' '/usr/local/share/pixmaps/gnome-commander/gnome_cmd_arrow_down.xpm'
 /usr/bin/install -c -m 644 'gnome_cmd_arrow_up.xpm' '/usr/local/share/pixmaps/gnome-commander/gnome_cmd_arrow_up.xpm'
 /usr/bin/install -c -m 644 'gnome-commander.xpm' '/usr/local/share/pixmaps/gnome-commander/gnome-commander.xpm'
 /usr/bin/install -c -m 644 'internal-viewer.xpm' '/usr/local/share/pixmaps/gnome-commander/internal-viewer.xpm'
 /usr/bin/install -c -m 644 'menu_bookmark.xpm' '/usr/local/share/pixmaps/gnome-commander/menu_bookmark.xpm'
 /usr/bin/install -c -m 644 'nautilus.svg' '/usr/local/share/pixmaps/gnome-commander/nautilus.svg'
 /usr/bin/install -c -m 644 'overlay_symlink.xpm' '/usr/local/share/pixmaps/gnome-commander/overlay_symlink.xpm'
 /usr/bin/install -c -m 644 'overlay_umount.xpm' '/usr/local/share/pixmaps/gnome-commander/overlay_umount.xpm'
 /usr/bin/install -c -m 644 'parent_dir.xpm' '/usr/local/share/pixmaps/gnome-commander/parent_dir.xpm'
 /usr/bin/install -c -m 644 'python.svg' '/usr/local/share/pixmaps/gnome-commander/python.svg'
 /usr/bin/install -c -m 644 'root_dir.xpm' '/usr/local/share/pixmaps/gnome-commander/root_dir.xpm'
 /usr/bin/install -c -m 644 'rotate-180-16.xpm' '/usr/local/share/pixmaps/gnome-commander/rotate-180-16.xpm'
 /usr/bin/install -c -m 644 'rotate-270-16.xpm' '/usr/local/share/pixmaps/gnome-commander/rotate-270-16.xpm'
 /usr/bin/install -c -m 644 'rotate-90-16.xpm' '/usr/local/share/pixmaps/gnome-commander/rotate-90-16.xpm'
 /usr/bin/install -c -m 644 'toggle_horizontal.xpm' '/usr/local/share/pixmaps/gnome-commander/toggle_horizontal.xpm'
 /usr/bin/install -c -m 644 'toggle_vertical.xpm' '/usr/local/share/pixmaps/gnome-commander/toggle_vertical.xpm'
 /usr/bin/install -c -m 644 'terminal.svg' '/usr/local/share/pixmaps/gnome-commander/terminal.svg'
make[3]: Leaving directory `/home/dez/Desktop/downloads/gc127/pixmaps'
make[2]: Leaving directory `/home/dez/Desktop/downloads/gc127/pixmaps'
make[1]: Leaving directory `/home/dez/Desktop/downloads/gc127/pixmaps'
Making install in doc
make[1]: Entering directory `/home/dez/Desktop/downloads/gc127/doc'
make[2]: Entering directory `/home/dez/Desktop/downloads/gc127/doc'
make[2]: Nothing to be done for `install-exec-am'.
/bin/bash ../mkinstalldirs /usr/local/share/gnome/help/gnome-commander/C
mkdir -p -- /usr/local/share/gnome/help/gnome-commander/C
/usr/bin/install -c -m 644 C/legal.xml /usr/local/share/gnome/help/gnome-commander/C/legal.xml
/usr/bin/install -c -m 644 C/gnome-commander.xml /usr/local/share/gnome/help/gnome-commander/C/gnome-commander.xml
/bin/bash ../mkinstalldirs /usr/local/share/gnome/help/gnome-commander/C/figures/
mkdir -p -- /usr/local/share/gnome/help/gnome-commander/C/figures/
/usr/bin/install -c -m 644 C/figures/create_archive.png /usr/local/share/gnome/help/gnome-commander/C/figures/create_archive.png
/usr/bin/install -c -m 644 C/figures/dev_cd.png /usr/local/share/gnome/help/gnome-commander/C/figures/dev_cd.png
/usr/bin/install -c -m 644 C/figures/extract_archive.png /usr/local/share/gnome/help/gnome-commander/C/figures/extract_archive.png
/usr/bin/install -c -m 644 C/figures/gnome-commander_dialog_adv_rename.png /usr/local/share/gnome/help/gnome-commander/C/figures/gnome-commander_dialog_adv_rename.png
/usr/bin/install -c -m 644 C/figures/gnome-commander_dialog_bookmark.png /usr/local/share/gnome/help/gnome-commander/C/figures/gnome-commander_dialog_bookmark.png
/usr/bin/install -c -m 644 C/figures/gnome-commander_dialog_file_metadata.png /usr/local/share/gnome/help/gnome-commander/C/figures/gnome-commander_dialog_file_metadata.png
/usr/bin/install -c -m 644 C/figures/gnome-commander_dialog_file_permissions.png /usr/local/share/gnome/help/gnome-commander/C/figures/gnome-commander_dialog_file_permissions.png
/usr/bin/install -c -m 644 C/figures/gnome-commander_dialog_file_properties.png /usr/local/share/gnome/help/gnome-commander/C/figures/gnome-commander_dialog_file_properties.png
/usr/bin/install -c -m 644 C/figures/gnome-commander_dialog_keyboard_shortcuts.png /usr/local/share/gnome/help/gnome-commander/C/figures/gnome-commander_dialog_keyboard_shortcuts.png
/usr/bin/install -c -m 644 C/figures/gnome-commander_dialog_remote_connections.png /usr/local/share/gnome/help/gnome-commander/C/figures/gnome-commander_dialog_remote_connections.png
/usr/bin/install -c -m 644 C/figures/gnome-commander_dialog_remote_server.png /usr/local/share/gnome/help/gnome-commander/C/figures/gnome-commander_dialog_remote_server.png
/usr/bin/install -c -m 644 C/figures/gnome-commander_dialog_search.png /usr/local/share/gnome/help/gnome-commander/C/figures/gnome-commander_dialog_search.png
/usr/bin/install -c -m 644 C/figures/gnome-commander_options_confirmation.png /usr/local/share/gnome/help/gnome-commander/C/figures/gnome-commander_options_confirmation.png
/usr/bin/install -c -m 644 C/figures/gnome-commander_options_devices.png /usr/local/share/gnome/help/gnome-commander/C/figures/gnome-commander_options_devices.png
/usr/bin/install -c -m 644 C/figures/gnome-commander_options_filters.png /usr/local/share/gnome/help/gnome-commander/C/figures/gnome-commander_options_filters.png
/usr/bin/install -c -m 644 C/figures/gnome-commander_options_format.png /usr/local/share/gnome/help/gnome-commander/C/figures/gnome-commander_options_format.png
/usr/bin/install -c -m 644 C/figures/gnome-commander_options_general.png /usr/local/share/gnome/help/gnome-commander/C/figures/gnome-commander_options_general.png
/usr/bin/install -c -m 644 C/figures/gnome-commander_options_layout.png /usr/local/share/gnome/help/gnome-commander/C/figures/gnome-commander_options_layout.png
/usr/bin/install -c -m 644 C/figures/gnome-commander_options_network.png /usr/local/share/gnome/help/gnome-commander/C/figures/gnome-commander_options_network.png
/usr/bin/install -c -m 644 C/figures/gnome-commander_options_programs.png /usr/local/share/gnome/help/gnome-commander/C/figures/gnome-commander_options_programs.png
/usr/bin/install -c -m 644 C/figures/gnome-commander_window.png /usr/local/share/gnome/help/gnome-commander/C/figures/gnome-commander_window.png
/usr/bin/install -c -m 644 C/figures/mounting.png /usr/local/share/gnome/help/gnome-commander/C/figures/mounting.png
/bin/bash ../mkinstalldirs /usr/local/share/omf/gnome-commander
mkdir -p -- /usr/local/share/omf/gnome-commander
/usr/bin/install -c -m 644 gnome-commander-C.omf /usr/local/share/omf/gnome-commander/gnome-commander-C.omf
scrollkeeper-update -p /var/lib/rarian -o /usr/local/share/omf/gnome-commander
test -z "/usr/local/share/man/man1" || /bin/mkdir -p "/usr/local/share/man/man1"
 /usr/bin/install -c -m 644 './gnome-commander.1' '/usr/local/share/man/man1/gnome-commander.1'
make[2]: Leaving directory `/home/dez/Desktop/downloads/gc127/doc'
make[1]: Leaving directory `/home/dez/Desktop/downloads/gc127/doc'
Making install in data
make[1]: Entering directory `/home/dez/Desktop/downloads/gc127/data'
make[2]: Entering directory `/home/dez/Desktop/downloads/gc127/data'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/applications" || /bin/mkdir -p "/usr/local/share/applications"
 /usr/bin/install -c -m 644 'gnome-commander.desktop' '/usr/local/share/applications/gnome-commander.desktop'
make[2]: Leaving directory `/home/dez/Desktop/downloads/gc127/data'
make[1]: Leaving directory `/home/dez/Desktop/downloads/gc127/data'
Making install in tests
make[1]: Entering directory `/home/dez/Desktop/downloads/gc127/tests'
make[2]: Entering directory `/home/dez/Desktop/downloads/gc127/tests'
make[3]: Entering directory `/home/dez/Desktop/downloads/gc127/tests'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/dez/Desktop/downloads/gc127/tests'
make[2]: Leaving directory `/home/dez/Desktop/downloads/gc127/tests'
make[1]: Leaving directory `/home/dez/Desktop/downloads/gc127/tests'
make[1]: Entering directory `/home/dez/Desktop/downloads/gc127'
make[2]: Entering directory `/home/dez/Desktop/downloads/gc127'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/dez/Desktop/downloads/gc127'
make[1]: Leaving directory `/home/dez/Desktop/downloads/gc127'
```



ok, so what do i do now??? it doesnt seem like theres any errors here either

---

### Post by Joeb454 on 2008-11-05
First off - I added some [noparse]```
 
```[/noparse] tags to your post to make it a little easier to read :)

As I mentioned - installing build-essential will install header files and compilers (mainly gcc and g++ for C/C++ etc.)

Apt-get build-dep <package>    <--- This installs the dependencies for the application you want to compile, though this only works if there is a version of it in the repositories :)

Finally - I knew to use gnome-commander because I did ```
apt-cache search gnome-commander
```


And your application should be installed - check the menu's for it, or try running ```
gnome-commander
``` From a terminal :)

---

### Post by stinger30au on 2008-11-05
ah ha! looks like it is working.


i had already installed the version out of the add remove programs and i thought i would run the program from accessories -> gnome commander and it is now saying i have version 1.2.7 and that is what i was looking for.

awesome!!!

Thanks so much JoeB454 , you are the best!

---

### Post by Joeb454 on 2008-11-05
No worries :)

See, compiling is easy ;) It's finding the dependencies manually that's the problem :(

You can mark your thread as solved too (Thread Tools > Mark as Solved)

---

