---
title: "Autotools under edgy"
date: 2006-10-19
forum: Programming Talk
---

### Post by loopback on 2006-10-19
Hi, I'm a fresh new Ubuntu user. I have a problem using autotools under Edgy. Checking out a test project from a CVS repository (gnome-hello from cvs.gnome.org) and running ./autogen produces this output (I tested also other GNOME projects a couple of project from sf.net and a small app written by myself, always same output)
```
luca@hoola-lap:~/CVS/gnome-hello$ ./autogen.sh 
/usr/bin/gnome-autogen.sh

checking for autoconf >= 2.53...

  testing autoconf2.50... 
not found.
  testing autoconf... 
found 2.60

checking for automake >= 1.9...

  testing automake-1.9... 
found 1.9.6

checking for libtool >= 1.5...

  testing libtoolize... 
found 1.5.22

checking for glib-gettext >= 2.2.0...

  testing glib-gettextize... 
found 2.12.4

checking for intltool >= 0.30...

  testing intltoolize... 
found 0.35.0

checking for pkg-config >= 0.14.0...

  testing pkg-config... 
found 0.20

checking for gnome-common >= 2.3.0...

  testing gnome-doc-common... 
found 2.12.0

Checking for required M4 macros...


Checking for forbidden M4 macros...

**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.


Processing ./configure.ac


Running libtoolize...

You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.

Running glib-gettextize... Ignore non-fatal messages.

Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.


Running intltoolize...


Running gnome-doc-common...


Running aclocal-1.9...

NONE:0: /usr/bin/m4: Premature end of frozen file
autom4te: /usr/bin/m4 failed with exit status: 1
aclocal-1.9: autom4te failed with exit status: 1
luca@hoola-lap:~/CVS/gnome-hello$ 
```
And these are the (relevant?) installed packages:
autoconf-2.60-1
automake1.9-1.9.6-4
autotools-dev-20060223.1
gnome-common-2.12.0-2ubuntu1
gnome-core-devel-1:2.14.2.1ubuntu1
gnome-doc-utils-0.8.0-0ubuntu1
m4-1.4.4-1
make-3.81-2
plus a bunch of -dev packages and the gcc/g++

I have already tried downgrading automake to older versions.
All these apps compile well under my other System (a Slackware). Please, let me know if you need some more detailed info.

Thanks.

---

### Post by loopback on 2006-10-19
Thanks to Sebastien and Daniel the problem is now solved :) My file system was corrupted and /usr/share/autoconf/autoconf/autoconf.m4f was unreadable (and libs.m4 too).

---

