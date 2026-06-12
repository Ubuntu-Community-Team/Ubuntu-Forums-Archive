---
title: "pkg-config ...old paths in cflags?"
date: 2007-11-23
forum: Programming Talk
---

### Post by tananaBrian on 2007-11-23
Hi,

  I'm trying to figure out how to purge old defunct paths from what pkg-config returns for some libraries.  For example, I had an old version of GTK+ built (preceded with a ./configure --prefix=<oldpath>) in an old path that is now gone.  I have GTK+ installed in the normal way now and it's in the normal /usr... path instead and the same thing applies to libglib v2.0 etcetera.  When I type:

  pkg-config --cflags gtk+-2.0

on the command line, it returns the old path info as well as the new:

-I/home/<old path>/external/include/glib-2.0 -I/usr/include/gtk-2.0 (etc)

  None of my LD_..._PATH variables have any of the old path stuff in them and I've grep'd all the .pc files in /usr/lib/pkgconfig and cannot find any references to the old path.  I've even unset PKG_CONFIG_PATH and ran pkg-config again and I get the same results.  Where is the old path info coming from?  I've removed those old tools from the machine and only want --cflags and --libs to return new information ...only!  Help!

Thanks,
Brian

:guitar:

---

### Post by volanin on 2007-11-23
Well, technically this old path does not matter.
Since it no longer exists, the compiler will simply ignore it.
But if you really want them to be gone, you can try the following:

```
$ sudo rm /usr/lib/pkgconfig/gtk+-2.0.pc
$ sudo aptitude reinstall libgtk2.0-dev

$ sudo rm /usr/lib/pkgconfig/glib-2.0.pc
$ sudo aptitude reinstall libglib2.0-dev

etc...
```


EDIT: Aggressive fix was too... aggressive! Edited out.

---

### Post by tananaBrian on 2007-11-23
Thanks, but no worky.  I just followed your rm and reinstall instructions for both gtk+-2.0 and glib-2.0 and pkg-config still returns includes with the old path stuff in it:

  pkg-config --cflags gtk+-2.0

returns the following,

-I/home/bd/asf/asf_tools/external/include/glib-2.0 -I/home/bd/asf/asf_tools/external/lib/glib-2.0/include -I/home/bd/asf/asf_tools/external/include/libpng12 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 

All those paths with "asf_tools" in them are gone and don't exist.

Running env | grep LD_  returns the following,

11:LD_LIBRARY_PATH=/usr/include:/usr/local/include:/usr/include/gtk-2.0:/usr/include/gtk-2.0/include:/usr/include/glib-2.0:/usr/include/:/usr/lib/glib-2.0:/usr/lib/glib-2.0/include:/usr/include/cairo:/usr/lib:/usr/local/lib
21:LD_RUN_PATH=/usr/include:/usr/local/include:/usr/include/gtk-2.0:/usr/include/gtk-2.0/include:/usr/include/glib-2.0:/usr/include/:/usr/lib/glib-2.0:/usr/lib/glib-2.0/include:/usr/include/cairo
30:LD_INCLUDE_PATH=/usr/include:/usr/local/include:/usr/include/gtk-2.0:/usr/include/gtk-2.0/include:/usr/include/glib-2.0:/usr/include/:/usr/lib/glib-2.0:/usr/lib/glib-2.0/include:/usr/include/cairo

Running echo $PKG_CONFIG_PATH returns the following,

/usr/include:/usr/local/include:/usr/include/gtk-2.0:/usr/include/gtk-2.0/include:/usr/include/glib-2.0:/usr/include/:/usr/lib/glib-2.0:/usr/lib/glib-2.0/include:/usr/include/cairo


As you can see, none of the above includes the asf_tools path.  If I go to /usr/lib/pkgconfig where all the .pc files live and do a grep on asf_tools, then no output results ...and if I edit the .pc files to check with my own eyes, there is no 'asf_tools' to be found.

If I run either of the following two commands, then again, the "asf_tools" string never shows up:

env | grep asf_tools

  or

declare | grep asf_tools

So where is pkg-config getting the paths that have the 'asf_tools' in them?  How do I "fix it" so only accurate paths are returned?

Signed,
Quite Puzzled

---

### Post by volanin on 2007-11-23
Well, well...
Grep for it in your whole system!
This will take some time to complete, but...
:)

```
$ sudo find / -type f -exec grep -H asf_tools {} \;
```

---

### Post by tananaBrian on 2007-11-23
...Wow.  That last set of commands blotto'd my pkg-config and reinstalling didn't fix it.  Had to copy pkgconfig.bak back to pkgconfig.  Works again, but same path issues as before...

bd

---

### Post by volanin on 2007-11-23
Sorry for that!
:)

---

### Post by MicahCarrick on 2007-11-26
If you look at the pc files, you'll find they use ${includedir} which is why grepping out the old path wouldn't work. Unfortunately, I don't know where $includedir is coming from, but maybe that will help.

---

