---
title: "Setting up Anjuta"
date: 2006-11-11
forum: Programming Talk
---

### Post by BrokeBody on 2006-11-11
I tried to make a new project in Anjuta and here's the output:

```
Creating /home/stefan/Projects/foobar-sample/ChangeLog ... Ok
Creating /home/stefan/Projects/foobar-sample/Makefile.am (using AutoGen)... Ok
Creating /home/stefan/Projects/foobar-sample/NEWS ... Ok
Creating /home/stefan/Projects/foobar-sample/README ... Ok
Creating /home/stefan/Projects/foobar-sample/autogen.sh (using AutoGen)... Ok
Creating /home/stefan/Projects/foobar-sample/configure.in (using AutoGen)... Ok
Creating /home/stefan/Projects/foobar-sample/foobar-sample.anjuta ... Ok
Creating /home/stefan/Projects/foobar-sample/.cvsignore ... Ok
Creating /home/stefan/Projects/foobar-sample/src/Makefile.am (using AutoGen)... Ok
Creating /home/stefan/Projects/foobar-sample/src/main.c (using AutoGen)... Ok
Creating /home/stefan/Projects/foobar-sample/src/.cvsignore ... Ok
Creating /home/stefan/Projects/foobar-sample/po/ChangeLog ... Ok
Creating /home/stefan/Projects/foobar-sample/po/POTFILES.in (using AutoGen)... Ok
Creating /home/stefan/Projects/foobar-sample/po/.cvsignore ... Ok
New project has been created successfully
Executing: sh -c 'cd /home/stefan/Projects/foobar-sample && ./autogen.sh'
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
ftp://ftp.gnu.org/pub/gnu/config/.

Making ./aclocal.m4 writable ...
Running aclocal  ...
aclocal:configure.in:24: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
Running autoheader...
Running automake --gnu  ...
configure.in: installing `./install-sh'
configure.in: installing `./missing'
src/Makefile.am: installing `./depcomp'
Makefile.am: installing `./INSTALL'
Makefile.am: installing `./COPYING'
Running autoconf ...
configure.in:24: error: possibly undefined macro: AM_GLIB_GNU_GETTEXT
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
Running ./configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
./configure: line 5798: AM_GLIB_GNU_GETTEXT: command not found
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: WARNING:  po/Makefile.in.in seems to ignore the --datarootdir setting
config.status: creating config.h
config.status: executing depfiles commands
Now type `make' to compile.
```

Now what? :-?

I just want to program, not to set up Anjuta for 3 hours! ](*,)

---

### Post by bigjimlad on 2006-11-11
Good luck... I really liked the look of Anjuta, but could never get the thing to actually *compile* anything...

Had more success with Geany.

---

### Post by BrokeBody on 2006-11-11
fixed ;)

---

### Post by JohnPhys on 2007-02-05
How did you fix it?  I'm having the same issues...

---

