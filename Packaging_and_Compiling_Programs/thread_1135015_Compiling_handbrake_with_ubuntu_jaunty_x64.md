---
title: "Compiling handbrake with ubuntu jaunty x64"
date: 2009-04-24
forum: Packaging and Compiling Programs
---

### Post by Polygon on 2009-04-24
Hi, i am trying to rewrite my guide for compiling handbrake for the new release

but i am getting this compile error: 

```
./contrib/lib/libx264.a(analyse.o): In function `x264_mb_analyse_transform_rd':
analyse.c:(.text+0x14dd6): undefined reference to `__divdi3'
./contrib/lib/libx264.a(set.o): In function `x264_validate_levels':
set.c:(.text+0x213): undefined reference to `__divdi3'
./contrib/lib/libx264.a(macroblock.o): In function `x264_noise_reduction_update':
macroblock.c:(.text+0xb60): undefined reference to `__udivdi3'
./contrib/lib/libxvidcore.a(plugin_2pass2.o): In function `.L80':
plugin_2pass2.c:(.text+0x1fa6): undefined reference to `__udivdi3'
./contrib/lib/libxvidcore.a(bitstream.o): In function `BitstreamWriteGroupOfVopHeader':
bitstream.c:(.text+0x49dd): undefined reference to `__divdi3'
bitstream.c:(.text+0x4a01): undefined reference to `__divdi3'
bitstream.c:(.text+0x4a56): undefined reference to `__divdi3'
bitstream.c:(.text+0x4a72): undefined reference to `__moddi3'
bitstream.c:(.text+0x4abf): undefined reference to `__moddi3'
bitstream.c:(.text+0x4b3f): undefined reference to `__moddi3'
collect2: ld returned 1 exit status
make: *** [HandBrakeCLI] Error 1

```

so yeah, i am not sure of what dependency i am missing....

here are the dependencies that are floating around for compiling it in previous versions (i have no idea which EXACT ones i need, as the handbrake devs do not provide any list)

build-essential
subversion
libdvdcss-dev 
libtool
automake

libx264-65
zlib1g-dev
libbz2-dev 
dvdbackup 
xmlto 
texinfo 
gfortran 
libgtk2.0-dev
nasm 
doxygen
libsdl1.2-dev 
gfortran-multilib
gcc-multilib 
g++-multilib 
libesd0-dev
libgtk1.2-dev 
libfftw3-dev 
electric-fence
libx264-dev
x264
libtheora-dev
intltool 
gettext
libgtk2.0-dev 
libglib2.0-dev
libhal-storage1
libhal-storage-dev
libhal-dev 
yasm
libgtkhtml3.14-dev

---

### Post by GrouchoMarx on 2009-04-25
Add the following PPA to your software sources:

[https://launchpad.net/~handbrake-ubuntu/+archive/ppa]("https://launchpad.net/~handbrake-ubuntu/+archive/ppa")

and then build-dep against the intrepid handbrake packages. I have not tested this against trunk, but it works with 0.9.3.

---

### Post by Polygon on 2009-04-26
sadly this does not work, as it appears i already have the dependencies installed, at least for 0.9.3

---

### Post by Polygon on 2009-04-26
update: i'm offically a moron, i had the svn folder on my intrepid install, which got copied over when i installed 64 bit intrepid (as opposed to the 32 bit intrepid install)

so the reason it was failing is cause half of it was compiled for 32 bit.

i deleted the folder, re-checked out and it worked fine.

---

### Post by munitor on 2009-09-05
I'm a noob and thought I would use this thread instead of start a new one since the subject is perfect. 

Tried to make HandBrake on jaunty x64 and don't get very far. The output from make is below. I ran make from the HandBrake-0.9.3 directory. 

echo "#ifndef HB_BUILD" > libhb/hbversion.h
echo "#define HB_BUILD 2009090501" >> libhb/hbversion.h
echo "#endif" >> libhb/hbversion.h
echo "#ifndef HB_VERSION" >> libhb/hbversion.h
echo "#define HB_VERSION \"svnexported\"" >> libhb/hbversion.h
echo "#endif" >> libhb/hbversion.h
echo "#ifndef HB_APPCAST_URL" >> libhb/hbversion.h
echo "#define APPCAST_URL \"http://handbrake.fr/appcast_unstable.xml\"" >> libhb/hbversion.h
echo "#endif" >> libhb/hbversion.h
( cd .. ; ./configure ; cd contrib ; cp -f ../config.jam . ; jam )

System: Linux
Endian: little

Don't run configure by hand, make runs it automatically.

No, really. That's it. Just type 'make' and hit return.

You're supposed to be building with make, not jam.
If you were going to use jam--which you shouldn't--you'd run:
 './jam' on a Mac, or
 'jam' on Linux or Windows

To make jam, boil fruit with sugar and an acid until pectins are released.

/bin/sh: jam: not found
make[1]: *** [.contrib] Error 127
make: *** [contrib/.contrib] Error 2

---

### Post by munitor on 2009-09-05
Okay, that was easy. Just needed to add jam. Seems obvious, now.

---

