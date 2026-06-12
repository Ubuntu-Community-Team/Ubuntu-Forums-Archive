---
title: "Anjuta it does not create any project"
date: 2005-10-25
forum: Programming Talk
---

### Post by nene on 2005-10-25
this is the error log:

Auto generating the Project: f ...
./autogen.sh
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Creating ./aclocal.m4 ...
Running glib-gettextize...  Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/local/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

Making ./aclocal.m4 writable ...
Running libtoolize...
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Running aclocal  ...
aclocal: configure.in: 22: macro `AM_GLIB_GNU_GETTEXT' not found in library
Running autoheader...
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader: 
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows to define a template without
autoheader: WARNING: `acconfig.h':
autoheader: 
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader: 		[Define if a function `main' is needed.])
autoheader: 
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
autoheader: error: AC_CONFIG_HEADERS not found in configure.in
Running automake --gnu  ...
automake: configure.in: installing `./install-sh'
automake: configure.in: installing `./missing'
automake: Makefile.am: installing `./INSTALL'
automake: Makefile.am: installing `./COPYING'
configure.in: 8: required file `./config.h.in' not found
Running autoconf ...
configure.in:7: error: possibly undefined macro: AM_INIT_AUTOMAKE
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.in:8: error: possibly undefined macro: AM_CONFIG_HEADER
configure.in:9: error: possibly undefined macro: AM_MAINTAINER_MODE
configure.in:13: error: possibly undefined macro: AM_PROG_CC_STDC
configure.in:22: error: possibly undefined macro: AM_GLIB_GNU_GETTEXT
configure.in:24: error: possibly undefined macro: AM_PROG_LIBTOOL
Running ./configure --enable-maintainer-mode ...
./configure: line 1250: syntax error near unexpected token `f,'
./configure: line 1250: `AM_INIT_AUTOMAKE(f, 0.1)'
Completed ... unsuccessful
Total time taken: 13 secs

---

