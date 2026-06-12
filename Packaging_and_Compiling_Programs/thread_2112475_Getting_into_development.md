---
title: "Getting into development"
date: 2013-02-04
forum: Packaging and Compiling Programs
---

### Post by FraggedLocust on 2013-02-04
I'm looking to get into development for Ubuntu and I chose tomboy as a beginning, but I'm having some trouble compiling using the GNOME Tomboy page (as I'll have to compile to test the program, correct?).

The problem I'm having is with the autogen.sh, as I haven't had any experience with the 'aclocal' thing.

I thought I had installed all the proper dev packages, is there anything I'm missing?

[Tomboy Developers Wiki]("https://live.gnome.org/Tomboy/Developers")
```
$ ./autogen.sh --prefix=/home/user/stage/tomboy --disable-scrollkeeper
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.68
checking for automake >= 1.9...
  testing automake-1.11... found 1.11.3
checking for libtool >= 1.5...
  testing libtoolize... found 2.4.2
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.35.4
checking for intltool >= 0.30...
  testing intltoolize... found 0.50.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.26
checking for gnome-doc-utils >= 0.4.2...
  testing gnome-doc-prepare... found 0.20.10
Checking for required M4 macros...
Checking for forbidden M4 macros...
Processing ./configure.in
Running libtoolize...
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: You should add the contents of the following files to `aclocal.m4':
libtoolize:   `/usr/share/aclocal/libtool.m4'
libtoolize:   `/usr/share/aclocal/ltoptions.m4'
libtoolize:   `/usr/share/aclocal/ltversion.m4'
libtoolize:   `/usr/share/aclocal/ltsugar.m4'
libtoolize:   `/usr/share/aclocal/lt~obsolete.m4'
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.in and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
Running glib-gettextize... Ignore non-fatal messages.
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/local/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running gnome-doc-prepare...
You should add the contents of '/usr/share/aclocal/gnome-doc-utils.m4' to 'aclocal.m4'.
Running aclocal-1.11...
configure.in:33: warning: macro `AM_GCONF_SOURCE_2' not found in library
Running autoconf...
configure.in:33: error: possibly undefined macro: AM_GCONF_SOURCE_2
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.

```

---

### Post by mc4man on 2013-02-05
Install libgconf2-dev

---

