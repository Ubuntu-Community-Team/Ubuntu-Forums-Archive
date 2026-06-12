---
title: "Help with Anjuta!!!"
date: 2005-07-30
forum: Programming Talk
---

### Post by grofaz on 2005-07-30
Will someone please help me get anjuta working? What am I doing wrong? How do I set up anjuta so it will compile and build?

Auto generating the Project: hiccup ...
./autogen.sh
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Creating ./aclocal.m4 ...
Running gettextize...  Ignore non-fatal messages.
  autopoint --force
autopoint: *** cvs program not found
autopoint: *** Stop.
Making ./aclocal.m4 writable ...
Running libtoolize...
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Running aclocal -I macros  ...
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
Running automake --gnu  ...
automake: configure.in: installing `./install-sh'
automake: configure.in: installing `./mkinstalldirs'
automake: configure.in: installing `./missing'
automake: Makefile.am: installing `./INSTALL'
automake: Makefile.am: installing `./COPYING'
configure.in: 80: required file `./ABOUT-NLS' not found
Makefile.am:6: required directory ./intl does not exist

**Error**: `automake' failed. Please fix the warnings
(probably missing development files) and try again.
Running ./configure --enable-maintainer-mode --enable-compile-warnings ...
./macros/autogen.sh: line 235: ./configure: No such file or directory
Completed ... unsuccessful
Total time taken: 6 secs

Very frustrating!

regards,
grofaz

---

### Post by lordphoenix on 2005-08-07
I have exactly same problem and never succedded in finding a solution is anybody can help us?

---

### Post by black hole sun on 2005-08-07
[QUOTE=lordphoenix]I have exactly same problem and never succedded in finding a solution is anybody can help us?[/QUOTE]
 Install automake 1.9; then run

sudo update-alternatives --config automake and select version 1.9 as default

---

### Post by Dimple on 2005-08-08
I keep getting these errors:
> 
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Creating ./aclocal.m4 ...
Running gettextize...  Ignore non-fatal messages.
  autopoint --force
autopoint: *** cvs program not found
autopoint: *** Stop.
Making ./aclocal.m4 writable ...
Running libtoolize...
Running aclocal -I macros  ...
macros/linger.m4:4: warning: underquoted definition of AC_STRUCT_LINGER
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
macros/gnome-cxx-check.m4:2: warning: underquoted definition of GNOME_CHECK_CXX
macros/check-utmp.m4:11: warning: underquoted definition of AC_CHECK_UTMP
/usr/share/aclocal/vorbis.m4:9: warning: underquoted definition of XIPH_PATH_VORBIS
/usr/share/aclocal/smpeg.m4:13: warning: underquoted definition of AM_PATH_SMPEG/usr/share/aclocal/pkg.m4:5: warning: underquoted definition of PKG_CHECK_MODULES
/usr/share/aclocal/aalib.m4:12: warning: underquoted definition of AM_PATH_AALIBRunning autoheader...
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader:
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows to define a template without
autoheader: WARNING: `acconfig.h':
autoheader:
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader:             [Define if a function `main' is needed.])
autoheader:
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
Running automake --gnu  ...
configure.in:110: required file `intl/Makefile.in' not found
configure.in:36: required file `./ABOUT-NLS' not found
Makefile.am:6: required directory ./intl does not exist

**Error**: `automake' failed. Please fix the warnings
(probably missing development files) and try again.
Running ./configure --enable-maintainer-mode --enable-compile-warnings ...
./macros/autogen.sh: line 235: ./configure: Tiedostoa tai hakemistoa ei ole


What should i do?

---

### Post by grofaz on 2005-08-09
I fixed most all of my build errors by installing all the recommended and suggested packages in synaptic. That is when you use synaptic to install anjuta, right click on anjuta and you can scroll down to the bottom of the pop up menu and select "Mark recommended for installation" and "Mark suggested for installation" and install everything you can. That cleared up most of my difficulties. Also I suggest installing devhelp and start reading. Lot's of info to absorb. Good luck!

---

### Post by Unaha-Closp on 2006-12-14
> **black hole sun said:**
> Install automake 1.9; then run

sudo update-alternatives --config automake and select version 1.9 as default

Thank you * 1e6, after installing every package under the sun this worked.

---

