---
title: "Can't Build Pango: Grep Error"
date: 2012-01-01
forum: Packaging and Compiling Programs
---

### Post by dodle on 2012-01-01
I'm trying to build pango for MinGW, so it isn't directly related to Ubuntu, but it is a Unix-like environment. libtool appears to be passing a bad argument to grep, I've looked all through the libtool and Makefiles and can't figure out what the problem is. Here is the output:

```
make[4]: Entering directory `/mingw/Compiling/pango-1.29.5/build-win32/pango'
  CCLD   libpangocairo-1.0.la
/bin/grep: invalid option -- p
Usage: /bin/grep [OPTION]... PATTERN [FILE]...
Try `/bin/grep --help' for more information.
```

The offending line appears to be somewhere around here in the Makefile of the pango subdirectory
(<top-build-dir>/pango/Makefile):
```
libpangocairo-1.0.la: $(libpangocairo_1_0_la_OBJECTS) $(libpangocairo_1_0_la_DEPENDENCIES) 
	$(libpangocairo_1_0_la_LINK) $(am_libpangocairo_1_0_la_rpath) $(libpangocairo_1_0_la_OBJECTS) $(libpangocairo_1_0_la_LIBADD) $(LIBS)
```

...but I can't figure out how to fix it. I've searched all over the internet but haven't been able to find anything about an invalid "p" option for grep.

```
$ grep --version
GNU grep 2.5.4

Copyright (C) 2009 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
```

```
$ ./libtool --version
libtool (GNU libtool) 2.4
Written by Gordon Matzigkeit <gord@gnu.ai.mit.edu>, 1996

Copyright (C) 2010 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```


**----- EDIT -----**

I decided to see if I could reproduce the error on Ubuntu, but I can't even get it to recognize that Glib is installed:

```
...
checking for CAIRO... yes
checking which cairo font backends could be used... freetype 
checking for GLIB... no
configure: error: 
*** Glib 2.31.0 or better is required. The latest version of
*** Glib is always available from ftp://ftp.gtk.org/.
```

```
$ sudo apt-get install libglib2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglib2.0-dev is already the newest version.
```


**----- EDIT -----**

Oh, I see the problem here:
```
$ apt-cache show libglib2.0-dev
...
...
Version: 2.28.6-0ubuntu1
...
```

Guess, I'll either need to upgrade Glib or try an older version of Pango.


**----- EDIT -----**

v1.28.4 compiled fine on Ubuntu so I tried it with MinGW, but it is still complaining about an invalid option "p" when trying to create [color=blue]libpangocairo-1.0.la[/color], *sigh*.

---

