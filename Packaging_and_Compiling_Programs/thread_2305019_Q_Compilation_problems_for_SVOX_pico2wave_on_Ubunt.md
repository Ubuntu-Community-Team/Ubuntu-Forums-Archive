---
title: "Q: Compilation problems for SVOX pico2wave on Ubuntu 14.04"
date: 2015-12-02
forum: Packaging and Compiling Programs
---

### Post by sm535 on 2015-12-02
I am probably committing a BBS sin, but I posted this same question on the Assistive Technology forum, but it appears there is no real programming related discussion on that forum. So, I am reposting it in this forum hoping someone can help me. 

I am trying to compile pico2wave on 14.04 (because of some changes that I made in the source). As described [here]("https://www.redhat.com/archives/blinux-list/2011-March/msg00022.html"), I downloaded the source from Debian git repo: 

```
git clone -b upstream+patches git://git.debian.org/collab-maint/svox.git  svox-pico
```

Here is my autogen.sh 

```
#!/bin/sh
set -v
export PATH=.:$PATH

#created by aclocal
rm -rf autom4te.cache
rm -f aclocal.m4

#created by libtoolize
rm -rf m4
rm -f ltmain.sh

#created by autoconf
rm -f configure

#created by automake
rm -f install-sh missing depcomp Makefile.in config.guess config.sub

#created by ./configure
rm -rf .deps
rm -f Makefile config.log config.status libtool

if [ "$1" = "clean" ]; then
    exit
fi

IPATHS="-I lib"

aclocal $IPATHS
libtoolize
autoconf $IPATHS
automake --add-missing

rm -rf autom4te.cache

echo "Now run ./configure and then make."
exit 0
```

My configure.in is as below: 

```
dnl Process this file with autoconf to produce a configure script.

AC_PREREQ(2.59)

AC_INIT([svox], [1.0], [math.parent@gmail.com])

AM_INIT_AUTOMAKE([1.9 foreign])
AUTOMAKE_OPTIONS([subdir-objects])

AC_PROG_CC
LT_INIT
AC_PROG_LIBTOOL

AC_CONFIG_FILES([Makefile])
AC_OUTPUT

AC_CONFIG_MACRO_DIR([m4])

AC_CHECK_LIB(popt, poptGetContext)

```

I ran ./autogen.sh from pico directory, but got the following warnings and  errors: 

```
$ ./autogen.sh

#created by aclocal
rm -rf autom4te.cache
rm -f aclocal.m4

#created by libtoolize
rm -rf m4
rm -f ltmain.sh

#created by autoconf
rm -f configure

#created by automake
rm -f install-sh missing depcomp Makefile.in config.guess config.sub

#created by ./configure
rm -rf .deps
rm -f Makefile config.log config.status libtool

if [ "$1" = "clean" ]; then
    exit
fi

IPATHS="-I lib"

aclocal $IPATHS
aclocal: warning: autoconf input should be named 'configure.ac', not 'configure.in'
aclocal: error: couldn't open directory 'm4': No such file or directory
libtoolize
libtoolize: putting auxiliary files in `.'.
libtoolize: linking file `./ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: linking file `m4/libtool.m4'
libtoolize: linking file `m4/ltoptions.m4'
libtoolize: linking file `m4/ltsugar.m4'
libtoolize: linking file `m4/ltversion.m4'
libtoolize: linking file `m4/lt~obsolete.m4'
autoconf $IPATHS
configure.in:7: error: possibly undefined macro: AM_INIT_AUTOMAKE
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.in:12: error: possibly undefined macro: AC_PROG_LIBTOOL
automake --add-missing
automake: warning: autoconf input should be named 'configure.ac', not 'configure.in'
configure.in: error: no proper invocation of AM_INIT_AUTOMAKE was found.
configure.in: You should verify that configure.in invokes AM_INIT_AUTOMAKE,
configure.in: that aclocal.m4 is present in the top-level directory,
configure.in: and that aclocal.m4 was recently regenerated (using aclocal)
Makefile.am: error: required file './NEWS' not found
Makefile.am: error: required file './README' not found
Makefile.am: error: required file './AUTHORS' not found
Makefile.am: error: required file './ChangeLog' not found
automake: warning: autoconf input should be named 'configure.ac', not 'configure.in'
Makefile.am:5: error: Libtool library used but 'LIBTOOL' is undefined
Makefile.am:5:   The usual way to define 'LIBTOOL' is to add 'LT_INIT'
Makefile.am:5:   to 'configure.in' and run 'aclocal' and 'autoconf' again.
Makefile.am:5:   If 'LT_INIT' is in 'configure.in', make sure
Makefile.am:5:   its definition is in aclocal's search path.
Makefile.am:6: warning: source file 'lib/picoacph.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
automake: warning: possible forward-incompatibility.
automake: At least a source file is in a subdirectory, but the 'subdir-objects'
automake: automake option hasn't been enabled.  For now, the corresponding output
automake: object file(s) will be placed in the top-level directory.  However,
automake: this behaviour will change in future Automake versions: they will
automake: unconditionally cause object files to be placed in the same subdirectory
automake: of the corresponding sources.
automake: You are advised to start using 'subdir-objects' option throughout your
automake: project, to avoid future incompatibilities.
Makefile.am:6: warning: source file 'lib/picoapi.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picobase.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picocep.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picoctrl.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picodata.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picodbg.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picoextapi.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picofftsg.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picokdbg.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picokdt.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picokfst.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picoklex.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picoknow.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picokpdf.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picokpr.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picoktab.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picoos.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picopal.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picopam.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picopr.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picorsrc.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picosa.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picosig.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picosig2.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picospho.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picotok.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picotrns.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:6: warning: source file 'lib/picowa.c' is in a subdirectory,
Makefile.am:6: but option 'subdir-objects' is disabled
Makefile.am:83: warning: source file 'bin/pico2wave.c' is in a subdirectory,
Makefile.am:83: but option 'subdir-objects' is disabled
Makefile.am: installing './depcomp'
/usr/share/automake-1.14/am/depend2.am: error: am__fastdepCC does not appear in AM_CONDITIONAL
/usr/share/automake-1.14/am/depend2.am:   The usual way to define 'am__fastdepCC' is to add 'AC_PROG_CC'
/usr/share/automake-1.14/am/depend2.am:   to 'configure.in' and run 'aclocal' and 'autoconf' again
/usr/share/automake-1.14/am/depend2.am: error: AMDEP does not appear in AM_CONDITIONAL
/usr/share/automake-1.14/am/depend2.am:   The usual way to define 'AMDEP' is to add one of the compiler tests
/usr/share/automake-1.14/am/depend2.am:     AC_PROG_CC, AC_PROG_CXX, AC_PROG_OBJC, AC_PROG_OBJCXX,
/usr/share/automake-1.14/am/depend2.am:     AM_PROG_AS, AM_PROG_GCJ, AM_PROG_UPC
/usr/share/automake-1.14/am/depend2.am:   to 'configure.in' and run 'aclocal' and 'autoconf' again

rm -rf autom4te.cache

echo "Now run ./configure and then make."
Now run ./configure and then make.
exit 0
```

The first error from aclocal says that m4 does nor exist. But it does in  the current directory. libtoolize seems to have found it. I am not sure  how to fix this and subsequent errors. Any help will be greatly  appreciated. 

Thanks very much.

---

### Post by howefield on 2015-12-02
Thread moved to the "*Packaging and Compiling Programs*" forum.

---

