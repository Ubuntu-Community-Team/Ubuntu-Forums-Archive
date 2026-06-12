---
title: "I spend more time packaging than writing program"
date: 2010-08-16
forum: Packaging and Compiling Programs
---

### Post by danwsc on 2010-08-16
Hi,

Well to date, almost as much.  Anybody knows what is wrong with this please?  These messages were from doing a 
$sudo pbuilder build *.dsc

configure.ac is attached.

Regards.

I: using fakeroot in build.
I: Current time: Tue Aug 17 00:52:31 SGT 2010
I: pbuilder-time-stamp: 1281977551
I: Building the build Environment
I: extracting base tarball [/var/cache/pbuilder/base.tgz]
I: creating local configuration
I: copying local configuration
I: mounting /proc filesystem
I: mounting /dev/pts filesystem
I: Mounting /home/bloomingdalebear/pbuilder/result
I: policy-rc.d already exists
I: Obtaining the cached apt archive contents
I: Installing the build-deps
I: user script /var/cache/pbuilder/build//11548/tmp/hooks/D70results starting
Executing hook: tmp/hooks/D70results
dpkg-scanpackages: info: Wrote 0 entries to output Packages file.
Ign file: ./ Release.gpg
Ign file: ./ Release
Ign file: ./ Packages
Ign file: ./ Packages
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release [65.9kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages [1353kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages [7971B]             
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages [5133kB]              
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages [190kB]             
Fetched 6750kB in 25s (264kB/s)                                                
Reading package lists... Done
I: user script /var/cache/pbuilder/build//11548/tmp/hooks/D70results finished
 -> Attempting to satisfy build-dependencies
 -> Creating pbuilder-satisfydepends-dummy package
Package: pbuilder-satisfydepends-dummy
Version: 0.invalid.0
Architecture: i386
Maintainer: Debian Pbuilder Team <pbuilder-maint@lists.alioth.debian.org>
Description: Dummy package to satisfy dependencies with aptitude - created by pbuilder
 This package was created automatically by pbuilder and should
Depends: debhelper (>= 7), autotools-dev
dpkg-deb: building package `pbuilder-satisfydepends-dummy' in `/tmp/satisfydepends-aptitude/pbuilder-satisfydepends-dummy.deb'.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
aptitude is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Selecting previously deselected package pbuilder-satisfydepends-dummy.
(Reading database ... 10668 files and directories currently installed.)
Unpacking pbuilder-satisfydepends-dummy (from .../pbuilder-satisfydepends-dummy.deb) ...
dpkg: dependency problems prevent configuration of pbuilder-satisfydepends-dummy:
 pbuilder-satisfydepends-dummy depends on debhelper (>= 7); however:
  Package debhelper is not installed.
 pbuilder-satisfydepends-dummy depends on autotools-dev; however:
  Package autotools-dev is not installed.
dpkg: error processing pbuilder-satisfydepends-dummy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pbuilder-satisfydepends-dummy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  autotools-dev{a} bsdmainutils{a} debhelper{a} file{a} gettext{a} 
  gettext-base{a} groff-base{a} html2text{a} intltool-debian{a} 
  libcroco3{a} libglib2.0-0{a} libmagic1{a} libpcre3{a} libxml2{a} 
  man-db{a} po-debconf{a} 
The following partially installed packages will be configured:
  pbuilder-satisfydepends-dummy 
The following packages are RECOMMENDED but will NOT be installed:
  curl cvs cvsnt libglib2.0-data libmail-sendmail-perl lynx 
  shared-mime-info wget xml-core 
0 packages upgraded, 16 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7497kB of archives. After unpacking 25.2MB will be used.
Writing extended state information... Done
debconf: delaying package configuration, since apt-utils is not installed
Selecting previously deselected package libmagic1.
(Reading database ... 10668 files and directories currently installed.)
Unpacking libmagic1 (from .../libmagic1_5.03-1ubuntu1_i386.deb) ...
Selecting previously deselected package file.
Unpacking file (from .../file_5.03-1ubuntu1_i386.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-14_i386.deb) ...
Selecting previously deselected package libpcre3.
Unpacking libpcre3 (from .../libpcre3_7.8-3_i386.deb) ...
Selecting previously deselected package libglib2.0-0.
Unpacking libglib2.0-0 (from .../libglib2.0-0_2.22.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package libxml2.
Unpacking libxml2 (from .../libxml2_2.7.5.dfsg-1ubuntu1_i386.deb) ...
Selecting previously deselected package libcroco3.
Unpacking libcroco3 (from .../libcroco3_0.6.1-2_i386.deb) ...
Selecting previously deselected package gettext-base.
Unpacking gettext-base (from .../gettext-base_0.17-8ubuntu2_i386.deb) ...
Selecting previously deselected package gettext.
Unpacking gettext (from .../gettext_0.17-8ubuntu2_i386.deb) ...
Selecting previously deselected package intltool-debian.
Unpacking intltool-debian (from .../intltool-debian_0.35.0+20060710.1_all.deb) ...
Selecting previously deselected package po-debconf.
Unpacking po-debconf (from .../po-debconf_1.0.16_all.deb) ...
Selecting previously deselected package groff-base.
Unpacking groff-base (from .../groff-base_1.20.1-5_i386.deb) ...
Selecting previously deselected package bsdmainutils.
Unpacking bsdmainutils (from .../bsdmainutils_6.1.10ubuntu4_i386.deb) ...
Selecting previously deselected package man-db.
Unpacking man-db (from .../man-db_2.5.6-2_i386.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_7.3.15ubuntu3_all.deb) ...
Selecting previously deselected package autotools-dev.
Unpacking autotools-dev (from .../autotools-dev_20090427.1_all.deb) ...
Setting up libmagic1 (5.03-1ubuntu1) ...

Setting up file (5.03-1ubuntu1) ...
Setting up html2text (1.3.2a-14) ...

Setting up libpcre3 (7.8-3) ...

Setting up libglib2.0-0 (2.22.2-0ubuntu1) ...

Setting up libxml2 (2.7.5.dfsg-1ubuntu1) ...

Setting up libcroco3 (0.6.1-2) ...

Setting up gettext-base (0.17-8ubuntu2) ...

Setting up gettext (0.17-8ubuntu2) ...

Setting up intltool-debian (0.35.0+20060710.1) ...
Setting up po-debconf (1.0.16) ...
Setting up groff-base (1.20.1-5) ...

Setting up bsdmainutils (6.1.10ubuntu4) ...
update-alternatives: using /usr/bin/bsd-write to provide /usr/bin/write (write) in auto mode.

Setting up man-db (2.5.6-2) ...
Building database of manual pages ...

Setting up debhelper (7.3.15ubuntu3) ...
Setting up autotools-dev (20090427.1) ...
Setting up pbuilder-satisfydepends-dummy (0.invalid.0) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

Current status: 0 broken [-1].
 -> Finished parsing the build-deps
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fakeroot is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
I: Copying back the cached apt archive contents
I: Copying source file
I: copying [vrdo_1.1-0ubuntu1.dsc]
I: copying [./vrdo_1.1.orig.tar.gz]
I: copying [./vrdo_1.1-0ubuntu1.diff.gz]
I: Extracting source
dpkg-source: warning: extracting unsigned source package (vrdo_1.1-0ubuntu1.dsc)
dpkg-source: info: extracting vrdo in vrdo-1.1
dpkg-source: info: unpacking vrdo_1.1.orig.tar.gz
dpkg-source: info: applying vrdo_1.1-0ubuntu1.diff.gz
I: Building the package
W: no hooks of type A found -- ignoring
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package vrdo
dpkg-buildpackage: source version 1.1-0ubuntu1
dpkg-buildpackage: source changed by Daniel Wong <danwsc@starhub.net.sg>
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp 
# Add here commands to clean up after the build process.
[ ! -f Makefile ] || /usr/bin/make distclean
make[1]: Entering directory `/tmp/buildd/vrdo-1.1'
/bin/bash ./config.status --recheck
running CONFIG_SHELL=/bin/bash /bin/bash ./configure --no-create --no-recursion
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
./configure: line 3646: gl_EARLY: command not found
./configure: line 3647: gl_INIT: command not found
checking for ranlib... ranlib
checking for pkg-config... no
checking for GST... configure: error: in `/tmp/buildd/vrdo-1.1':
configure: error: The pkg-config script could not be found or is too old.  Make sure it
is in your PATH or set the PKG_CONFIG environment variable to the full
path to pkg-config.

Alternatively, you may set the environment variables GST_CFLAGS
and GST_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

To get pkg-config, see <http://pkg-config.freedesktop.org/>.
See `config.log' for more details.
make[1]: *** [config.status] Error 1
make[1]: Leaving directory `/tmp/buildd/vrdo-1.1'
make: *** [clean] Error 2
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2
E: Failed autobuilding of package
W: no hooks of type C found -- ignoring
I: unmounting /home/bloomingdalebear/pbuilder/result filesystem
I: unmounting dev/pts filesystem
I: unmounting proc filesystem
I: cleaning the build env 
I: removing directory /var/cache/pbuilder/build//11548 and its subdirectories
bloomingdalebear@bloomingdalebear-desktop:~/160810/vrdo-pbuilder1$

---

### Post by danwsc on 2010-08-17
Just some more background to the problem.

The source compiles okay on my system.
But not on another system.
I can reclaim the source directory from the .tar.gz, .dsc and .diff.gz by using dpkg-source -x *.dsc as in the packaging guide.

Problem happens with the next step when I am trying to build the binary with pbuilder.

Thanks in advance.

---

### Post by SevenMachines on 2010-08-17
>   I spend more time packaging than writing program
It can feel like that i know :) But, once the packaging is done you don't need to do it again!

If it builds fine on your system but doesnt when using pbuilder then in general chances are you're missing a dependency in the Build-Depends: entry in your debian/control file. 
This is actually why running pbuilder (which uses a 'clean' installed system) is a good thing and is used to catch missing dependencies.

In this case it looks like you're using pkg-config but haven't specified the dependency on it in debian/control Build-Depends

---

### Post by danwsc on 2010-08-19
Hi, following your advice, I think I'm through the Build-Depends part.  Now there seems to be something else wrong in the make gnulib part.

.
.
.
gcc -DHAVE_CONFIG_H -I. -I../..  -I../../intl   -Wall         -pedantic -ansi -std=c99     -g -O2 -MT localcharset.o -MD -MP -MF .deps/localcharset.Tpo -c -o localcharset.o localcharset.c
In file included from localcharset.c:27:
./stdio.h:21: error: stray '@' in program
./stdio.h:21: error: stray '@' in program
In file included from ./stdio.h:40,
                 from localcharset.c:27:
/usr/lib/gcc/i486-linux-gnu/4.4.1/include/stdarg.h:40: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'typedef'
In file included from ./stdio.h:40,
                 from localcharset.c:27:
/usr/lib/gcc/i486-linux-gnu/4.4.1/include/stdarg.h:102: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'va_list'
In file included from localcharset.c:27:
./stdio.h:43:7: error: operator '&&' has no left operand
./stdio.h:101:5: error: #if with no expression
./stdio.h:107:8: error: operator '&&' has no left operand
./stdio.h:120:5: error: #if with no expression
./stdio.h:126:8: error: operator '&&' has no left operand
./stdio.h:139:5: error: #if with no expression
./stdio.h:146:8: error: operator '&&' has no left operand
./stdio.h:167:5: error: #if with no expression
./stdio.h:173:8: error: operator '&&' has no left operand
./stdio.h:186:5: error: #if with no expression
./stdio.h:202:5: error: #if with no expression
./stdio.h:218:5: error: #if with no expression
./stdio.h:233:5: error: #if with no expression
./stdio.h:248:5: error: #if with no expression
./stdio.h:264:5: error: #if with no expression
./stdio.h:280:5: error: #if with no expression
.
.
.

Looking inside the gnulib/lib/stdio.in.h, at line 19 onwards I get

#if __GNUC__ >= 3
@PRAGMA_SYSTEM_HEADER@
#endif

Any suggestions what to do please?

Regards.

---

### Post by SevenMachines on 2010-08-20
Sorry, i can't really tell, unlikely to be glib related and more likely what you're trying to compile though, a misplaced #endif there, a format error there, they can all lead to that sort of error, among other things.
If you've got a link to the source/packaging of what your trying to build though?

---

### Post by MrQuincle on 2010-08-20
Check what libraries/packages your executables are actually depending on:

[http://ubuntuforums.org/showpost.php?p=9730660&postcount=3](http://ubuntuforums.org/showpost.php?p=9730660&postcount=3)

You might start with including all of them and deleting them afterwards.

And, what also helps of course is to check beforehand that everything is available *before* you start to compile... I happen to use cmake and run into a clear error message most of the times, before it even attempts to build.

---

