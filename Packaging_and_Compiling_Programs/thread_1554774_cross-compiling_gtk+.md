---
title: "cross-compiling gtk+"
date: 2010-08-17
forum: Packaging and Compiling Programs
---

### Post by fiva on 2010-08-17
I'm using an Ubuntu 10.04 host to do developments for a Freescale i.MX27 board. Building the default configuration works fine. (building is done with Freescale's LTIB environment).Now, I would like to add gtk functionality to my build. These are the commands that were executed from the ltib script :

[FONT=Courier New]export PKG_CONFIG_PATH=%{_prefix}/lib/pkgconfig/
./configure --prefix=%{_prefix} --host=$CFGHOST --build=%{_build} 
make[/FONT]

These are the last lines of the console output :

[FONT=Courier New]checking for fd_set... yes, found in sys/types.h
checking for wchar.h... yes
checking for wctype.h... yes
checking for iswalnum... yes
checking if iswalnum() and friends are properly defined... yes
checking whether to build gmodulized gdk-pixbuf... yes
checking whether dynamic modules work... yes
checking for TIFFReadScanline in -ltiff... no
checking for TIFFWriteScanline in -ltiff... no
checking for TIFFFlushData in -ltiff34... no
configure: WARNING: *** TIFF plug-in will not be built (TIFF library not found) ***
configure: error:
*** Checks for TIFF loader failed. You can build without it by passing
*** --without-libtiff to configure but some programs using GTK+ may
*** not work properly
error: Bad exit status from /home/filip/i.MX27/ltib/tmp/rpm-tmp.64645 (%build)


RPM build errors:
    Bad exit status from /home/filip/i.MX27/ltib/tmp/rpm-tmp.64645 (%build)
Build time for gtk2: 7 seconds

Failed building gtk2
[/FONT]
Obviously, there's a problem finding the TIFF library. However, I checked and the TIFF library is installed (i.e. apt-get install libtiff4-dev returns "is already the newest version").
As a non-expert in Linux : can anyone point me in the good direction ? Probably a 'simple' problem of missing or incorrect paths ? Environment variables that are not correct ?

Thanks for help !

---

### Post by SevenMachines on 2010-08-17
it may be that it requires [libtiff3 (3.4?)]("ftp://ftp.remotesensing.org/pub/libtiff/old/") rather than libtiff4 would be my guess, i dont know. You may want to see if theres a newer version or cvs of whatever it is your trying to compile.
But in any case, in general, you can usually add configure options. look at
$ ./configure --help

you'll probably see some option like --with-tiff= or something like that where you can set the path to the tiff headers. probably some like --disable-tiff could be there too to turn it off completely.
I assume if you're actually cross compiling then you have all the relevant libraries *for the target platform* installed

---

