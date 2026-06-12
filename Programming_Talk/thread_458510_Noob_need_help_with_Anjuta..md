---
title: "Noob need help with Anjuta."
date: 2007-05-29
forum: Programming Talk
---

### Post by B0rat on 2007-05-29
I have opened Anjuta and selected a console C++ project. What i have now is the Hello World program. 

I select Build -> Compile and it compiles ok. However if I select Build -> Build I get:

make: no targets specified and no makefile found

I assume there is something simple wrong or I am doing something wrong.

This is my first plunge into C++ and Anjuta so I am in the unknown. I have compiled programs from source before but I really want to learn programming and Anjuta seems to be as good as most other apps out there.

If you can offer any advice, I'd sure appreciate it.

---

### Post by PandaGoat on 2007-05-29
You have to go to Build->Auto Generate.  You will probably get a few errors about missing stuff like automake, libtool, etc.  Use synaptic to install these and try again.

---

### Post by B0rat on 2007-05-30
I get these errors.... but I can't determine what is missing.

Auto generating the Project: hw ...
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
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

Making ./aclocal.m4 writable ...
Running libtoolize...
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Running aclocal  ...
aclocal: macro `AM_PROG_MKDIR_P' required but not defined
aclocal: macro `AM_PROG_MKDIR_P' required but not defined
Running autoheader...
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader: 
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows one to define a template without
autoheader: WARNING: `acconfig.h':
autoheader: 
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader: 		[Define if a function `main' is needed.])
autoheader: 
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
autoheader: error: AC_CONFIG_HEADERS not found in configure.in
Running automake --gnu  ...
configure.in: 8: required file `./config.h.in' not found
Running autoconf ...
Running ./configure --enable-maintainer-mode ...
./configure: line 1655: syntax error near unexpected token `hw,'
./configure: line 1655: `AM_INIT_AUTOMAKE(hw, 0.1)'
Completed ... unsuccessful
Total time taken: 2 secs

---

### Post by PandaGoat on 2007-05-30
Hmm.  It usually specifies what is missing if anything is.  Make sure you have automake installed, if it is try reinstalling it.  If all else fails try recreated the project.  I am not sure :(

---

### Post by B0rat on 2007-05-30
I installed automake 1.9 and that seemed to sort it. So atm i have automake 1.4, 1.8 and 1.9 installed.

PS Thank you for taking time to look at this for me ;)

---

