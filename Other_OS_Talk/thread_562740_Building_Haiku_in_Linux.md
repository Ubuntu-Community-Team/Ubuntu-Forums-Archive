---
title: "Building Haiku in Linux"
date: 2007-09-29
forum: Other OS Talk
---

### Post by RAV TUX on 2007-09-29
I have started here a cafe thread on building Haiku in Linux. Please use this thread to discuss building/using Haiku in Linux. 

refer to the Haiku homepage for more information if needed: [http://haiku-os.org/](http://haiku-os.org/)

 I began by following this directive:

1) Login as su

2)  Get subversion
```
apt-get install subversion
```3) compile the build tools:
```
apt-get install autoconf
``````
 apt-get install automake
``````
 apt-get install texinfo
``````
 apt-get install flex
``````
 apt-get install bison
``````
 apt-get install gawk
```4) fetching the build tools:
```
svn checkout svn://svn.berlios.de/haiku/haiku/trunk haiku
``````
svn checkout svn://svn.berlios.de/haiku/buildtools/trunk buildtools
```5)Building jam
```
cd  buildtools/jam  
make
./jam0 install
```6) since Haiku requires a modified version of jam check to see that you have the correct version of jam:
```
jam -v
```for example I checked my jam version and got these results:
```
Jam 2.5-haiku-20060813. OS=LINUX. Copyright 1993-2002 Christopher Seiwald.
```which is the correct version 

7)Building binutils:

for simplicity lets go with: 
> 2.95: Creates BeOS compatible binariesThe 2.95 command configuration is:
```
cd haiku 
./configure --build-cross-tools ../buildtools/


```This final step in building the binutils is where I am stuck btw:

here is what I get when I try this:
```
# cd haiku
bash: cd: haiku: No such file or directory
[/home/ravtux/buildtools/jam]# ./configure --build-cross-tools ../buildtools/
bash: ./configure: No such file or directory
```for the above directive see this link and also follow the comments:

[http://haiku-os.org/documents/dev/getting_linux_developer_tools](http://haiku-os.org/documents/dev/getting_linux_developer_tools)

also see the attached screenshots:

---

### Post by RAV TUX on 2007-09-29
here is some more information from the 'Read Me' file:
> 
Building on a non-BeOS platform
===============================

Please read the file 'ReadMe.cross-compile' before continuing. It describes
how to build the cross-compilation tools and configure the build system for
building Haiku. After following the instructions you can directly continue
with the section Building.


Configuring on BeOS
===================

Open a Terminal and change to your Haiku trunk folder. To configure the build
you can run configure like this:

  ./configure --target=TARGET

Where "TARGET" is the target platform that the compiled code should run on:
  * haiku (default)
  * r5
  * bone
  * dano (also for Zeta)

The configure script generates a file named "BuildConfig" in the "build"
directory. As long as configure is not modified (!), there is no need to call
it again. That is for re-building you only need to invoke jam (see below).
If you don't update the source tree very frequently, you may want to execute
'configure' after each update just to be on the safe side.


Building
========

Haiku can be built in either of two ways, as disk image file (e.g. for use
with emulators) or as installation in a directory.

Image File
----------

  jam -q haiku-image

This generates an image file named 'haiku.image' in your output directory
under 'generated/'.

VMware Image File
-----------------

  jam -q haiku-vmware-image

This generates an image file named 'haiku.vmdk' in your output
directory under 'generated/'.

Directory Installation
----------------------

  HAIKU_INSTALL_DIR=/Haiku jam -q install-haiku

Installs all Haiku components into the volume mounted at "/Haiku" and
automatically marks it as bootable. To create a partition in the first place
use DriveSetup and initialize it to BFS.

Note that installing Haiku in a directory only works as expected under BeOS,
but it is not yet supported under Linux and other non-BeOS platforms.

Building Components
-------------------

If you don't want to build the complete Haiku, but only a certain
app/driver/etc. you can specify it as argument to jam, e.g.:

  jam Pulse

Alternatively, you can 'cd' to the directory of the component you want to
build and run 'jam' from there.

You can also force rebuilding of a component by using the "-a" parameter:

  jam -a Pulse


Running
=======

Generally there are two ways of running Haiku. On real hardware using a
partition and on emulated hardware using an emulator like Bochs or QEmu.

On Real Hardware
----------------

If you have installed Haiku to its own partition you can include this
partition in your bootmanager and try to boot Haiku like any other OS you
have installed. To include a new partition in the BeOS bootmanager run this
in a Terminal:

  bootman

On Emulated Hardware
--------------------

For emulated hardware you should build disk image (see above). How to setup
this image depends on your emulater. A tutorial for Bochs on BeOS is below.
If you use QEmu, you can usually just provide the path to the image as
command line argument to the "qemu" executable.

Bochs
-----

Version 2.2 of Bochs for BeOS (BeBochs) can be downloaded from BeBits:

  [http://www.bebits.com/app/3324](http://www.bebits.com/app/3324)

The package installs to: /boot/apps/BeBochs2.2

You have to set up a configuration for Bochs. You should edit the ".bochsrc" to
include the following:

ata0-master: type=disk, path="/path/to/haiku.image", cylinders=122, heads=16, spt=63
boot: disk

Now you can start Bochs:

  $ cd /boot/apps/BeBochs2.2
  $ ./bochs

Answer with RETURN and with some patience you will see Haiku booting.
If booting into the graphical evironment fails you can try to hit "space" at the
very beginning of the boot process. The Haiku bootloader should then come up and
you can select some safe mode options.


Docbook documentation
=====================

Our documentation can be found in 'src/documentation/'. You can build it by
running 'jam' in that folder. The results will be stored in the 'generated/'
folder.

---

### Post by RAV TUX on 2007-09-29
This Read me is more specific to setting up the cross compiler:
> 
Building on a non-BeOS platform
===============================

We currently support these non-BeOS platforms:
 * Linux
 * FreeBSD
 * Mac OS X Intel (gcc 4 builds only)

To build Haiku on a non-BeOS platform you must first check out and build the
cross-compiler. The easiest method for doing so is to check it out in the
parent directory of your Haiku repository:

  svn checkout svn://svn.berlios.de/haiku/buildtools/trunk buildtools

You should now have a 'buildtools' folder that contains folders named
'binutils', 'gcc', and 'jam' among others.

Several other tools are required to build these build tools or are used by
Haiku's build system itself:
 * gcc and the binutils (as, ld, etc., required by gcc)
 * make (GNU make)
 * bison
 * flex and lex (usually a mini shell script invoking flex)
 * makeinfo (part of texinfo, needed for building gcc 4 only)
 * autoheader (part of autoconf, needed for building gcc)
 * gawk

Whether they are installed can be tested for instance by running them in the
shell with the "--version" parameter.

On Mac OS X a case-sensitive file system is required for the Haiku tree
(Disk Utility can be used to create a case-sensitive disk image of at least
3GB size), and the following darwin ports need to be installed:
 * expat
 * gawk
 * gettext
 * libiconv
 * gnuregex


Building Jam
============

Change to the buildtools folder and we will start to build 'jam' which is a
requirement for building Haiku. Run the following commands to generate and
install the tool:

  cd  buildtools/jam  
  make
  sudo ./jam0 install


Building binutils
=================

The binutils used by Haiku will be automatically generated according to the
initial configuration of the Haiku source and placed in the
'generated/cross-tools' directory of Haiku. Before generating the tools you
must consider the version required, there are essentially two choices:

  * 2.95: Creates BeOS compatible binaries
  * 4.x: Incompatible with BeOS, but theoretically more efficient binaries

Unless there is a pressing need, choose 2.95 as the latter option can cause
frequent build issues. The commands for configuration are,

GCC 2.95
--------

  cd haiku 
  ./configure --build-cross-tools ../buildtools/

GCC 4.x
-------

  cd haiku
  ./configure --build-cross-tools-gcc4 x86 ../buildtools/

The process can take quite some time, but when it finishes the build system is
fully configured and you are ready to compile your first Haiku image.

Instructions on how to build Haiku can be found in the section Building in the
'ReadMe' document.

---

### Post by RAV TUX on 2007-09-29
>  You should now have a 'buildtools' folder that contains folders named
'binutils', 'gcc', and 'jam' among others.

This I do have ;)

---

### Post by RAV TUX on 2007-09-29
unraveling the clues on building Haiku in Linux

a couple of more read-me's:

> How to build gcc-2.95.3 for BeOS under Linux (a cross-compiler), which 
will allow you to compile BeOS projects under Linux, i.e. the apps
that this compilers produces can only be executed on BeOS (not on Linux).

If all you are interested is compiling haiku on Linux, please refer to 
the file 'INSTALL-as-haiku-cross-compiler' instead (that's easier).

These instructions are required only if you want to compile something
(applications, libraries) on LINUX which should be executed on BeOS R5,
BONE or ZETA.

*** the major work of creating the cross-compiler and describing the
*** process how to build it has been done by Eric Petit <titer@m0k.org>, 
*** so if you think this cross-compiler is great, please tell him.

-----------------------------------------------------------------------
On your Linux-box, open a shell...

0 - Preparations
----------------
...and fetch the 'buildtools' module from the haiku SVN. You should then
have a 'buildtools' folder that contains folders named 'binutils' and
'gcc' (and this file, too!).

    cd buildtools/legacy

Now decide where you want to install the cross-compiler. The install 
folder will be referred to as $PREFIX. I suggest to install to 
/opt/cross-tools, but you can basically put it anywhere you like.

    export PREFIX=/opt/cross-tools

and add it the path:

    export PATH=$PATH:$PREFIX/bin

Create two folders for the headers and libraries, say $BEINC and
$BELIB:
    
    mkdir beinc
    export BEINC=$(pwd)/beinc
    mkdir belib
    export BELIB=$(pwd)/belib

Copy all contents from /boot/develop/lib/x86/ on your BeOS install to
$BELIBS on your Linux box (make sure symbolic links are followed). You
should have $BELIBS/libbe.so, etc.

Copy all contents from /boot/develop/headers/ on your BeOS install to
$BEINCS on your Linux box. You should have $BEINCS/be/AppKit.h, etc.


1 - Building binutils
---------------------
    mkdir binutils-obj
    cd binutils-obj
    CFLAGS="-O2" CXXFLAGS="-O2" ../binutils/configure --prefix=$PREFIX \
    --target=i586-pc-beos --disable-nls --enable-shared=yes
    make && make install
    cd ..

2 - Building gcc/g++
--------------------
    mkdir -p $PREFIX/lib/gcc-lib/i586-pc-beos/2.95.3-beos-041202
    mkdir gcc-obj
    cd gcc-obj
    CFLAGS="-O2" CXXFLAGS="-O2" ../gcc/configure --prefix=$PREFIX \
    --target=i586-pc-beos --disable-nls --enable-shared=yes \
    --enable-languages=c,c++ --with-headers=$BEINC --with-libs=$BELIB
    make cross && make install
    cd ..

Ok, now everything is compiled and installed, waiting to be used:

    i586-pc-beos-gcc test.c
    
would compile the file test.c with the fresh cross-compiler.

So have fun!

Please send questions & bug-reports to: Oliver Tappe <gcc@hirschkaefer.de>


> 
How to create a cross-compiler on LINUX (or any other supported build platform)
for haiku (information is copied from haiku's README):

Please chdir into haiku's base directory (the one where Jamrules and README live).

If you want to build the default (legacy, 2.95.3) gcc, do this:

  $ ./configure --build-cross-tools ../buildtools

One of the last output lines should tell you that the tools have been built
successfully.

If you're not interested in binary compatibility (or want to build for the PowerPC architecture), you can build gcc4 instead by doing this:

  $ ./configure --build-cross-tools-gcc4 <arch> ../buildtools

Replace "<arch>" with either "x86" or "ppc", depending on which of the two
architectures you want to build for.

---

### Post by Jucato on 2007-09-29
Wait, I'm confused... Isn't Haiku supposed to be a totally new/different OS? How is it that you're building it on Linux?

Oh, and btw, hi RAV! How's Cafe Linux and Oz Linux doing? :D

---

### Post by K.Mandla on 2007-09-29
Moved to Other OS Talk.

---

### Post by RAV TUX on 2007-09-29
> **Jucato said:**
> Wait, I'm confused... Isn't Haiku supposed to be a totally new/different OS? How is it that you're building it on Linux?



Pretty interesting isn't it, it can be built within Linux and even set up with a separate GRUB menu to boot into separately.


> **Jucato said:**
> 

Oh, and btw, hi RAV! How's Cafe Linux and Oz Linux doing? :D

CafeLinux is great, check it out for yourself:
[http://www.cafelinux.org/home/](http://www.cafelinux.org/home/)


Oz Linux is very active and can be downloaded:
[http://cafelinux.org/OzEnterprise/](http://cafelinux.org/OzEnterprise/)

> **K.Mandla said:**
> Moved to Other OS Talk.
This is unfortunate since Haiku can be built in Ubuntu.

---

### Post by RAV TUX on 2007-09-30
[http://pastebin.ca/720291](http://pastebin.ca/720291)

[http://pastebin.ca/720317](http://pastebin.ca/720317)

---

### Post by RAV TUX on 2007-09-30
YES!!! I am running Haiku in Linux!

---

### Post by RAV TUX on 2007-09-30
another

---

### Post by RAV TUX on 2007-09-30
Using Haiku in Linux, the next step is to install Haiku on my hard drive from Linux

---

### Post by Warren Watts on 2007-09-30
building Ubuntu haiku
troublesome at best
persistence leads to success

---

### Post by RAV TUX on 2007-09-30
> **Warren Watts said:**
> building Ubuntu haiku
troublesome at best
persistence leads to success

A classic Haiku
brings smile to face
using Haiku in Enlightenment

---

### Post by RAV TUX on 2007-09-30
> **Warren Watts said:**
> building Ubuntu haiku
troublesome at best
persistence leads to successThanks for the inspiration.

---

### Post by charlieg on 2007-11-24
Just wanted to say that the vmware image worked a treat.  God damn, the thing booted almost immediately.  Here's me, used to 1minute+ boots (from cold to desktop) with Ubuntu (and that's an improvement on what it used to be) and Haiku, as a VMWare image, booted in what I think was less than 3 seconds (or not far off).

The main problem is the vmware image comes without a web browser.  Unless I was missing something obvious, there was no way to install new applications, making the vmware a cool tech demo and not useful for anything more.  It looks like it's come a long way though, and I hope to see it enter the "market" as a usable OS in the not-very-distant future!

---

### Post by meborc on 2007-11-26
reading this thread answeres the age-old-question = how come RAV has so many beans :D ... well now i now 

on topic - haiku seems like a very promising project with concentrated group of developers... but if you are not going to contribute in code or test it, there is no point in installing it yet... for normal user this os needs to evolve another step...

i like that they put time in thinking about the solutions compared to the usual lets-hurry-and-get-it-done-with mentality :)

---

### Post by koki on 2007-12-03
> **charlieg said:**
> Just wanted to say that the vmware image worked a treat.  God damn, the thing booted almost immediately.  Here's me, used to 1minute+ boots (from cold to desktop) with Ubuntu (and that's an improvement on what it used to be) and Haiku, as a VMWare image, booted in what I think was less than 3 seconds (or not far off).

Sweet, isn't it? :)

> **charlieg said:**
> The main problem is the vmware image comes without a web browser.  Unless I was missing something obvious, there was no way to install new applications, making the vmware a cool tech demo and not useful for anything more.  It looks like it's come a long way though, and I hope to see it enter the "market" as a usable OS in the not-very-distant future!

Haiku does not have a browser yet. There is a BeOS port of Firefox that the [BeZilla team]("http://community.livejournal.com/bezilla") is working on to eventually get it to run in Haiku, and there is also an ongoing port of the webkit, which will at some point result in a broswer for Haiku.

If at this point you want to play with Haiku in VMWare, perhaps the best would be to try the Power Pack from HaikuWare.com, which includes the base OS plus a good number of (mostly) BeOS apps. Get it from here:

[http://www.haikuware.com/view-details/development/app-installation/74-weekly-super-pack-nov7th-rev22848](http://www.haikuware.com/view-details/development/app-installation/74-weekly-super-pack-nov7th-rev22848)

Enjoy!

---

### Post by erikf154 on 2008-07-16
When building Haiku (i.e. using HAIKU_INSTALL_DIR=/Haiku jam -q install-haiku), is it possible to optimize the compiling by using CFLAGS, if so -how?

---

