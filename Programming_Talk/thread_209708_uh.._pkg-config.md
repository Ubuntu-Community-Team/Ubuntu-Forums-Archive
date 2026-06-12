---
title: "uh.. pkg-config?"
date: 2006-07-05
forum: Programming Talk
---

### Post by mlind on 2006-07-05
I've setup devel environment so that all development libraries are installed on
chrooted enviroment, which is basically Dapper with ubuntu-minimal package
installed and bunch of libraries.

I can compile programs there nicely, but I'd like to compile programs from my
main environment, and use libraries & headers from chrooted environment.

I've got this almos working by using **PKG_CONFIG_PATH=/chroot/dapper-dev/usr/lib/pkgconfig**
when configuring packages, but what I don't get is how to tell pkg-config that
package prefix should be /chroot/dapper/dev...


For example
```

pkg-config --cflags glib-2.0
-I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include

```

that should be -I/chroot/dapper/dev/usr/include/glib-2.0 for my setup I presume?

I've only found  *--define-variable=prefix fooprefix* from pkg-config manual, but
there must be easier way to set that prefix for all .pc files on /chroot/dapper-dev/usr/lib/pkgconfig ?

---

### Post by nagilum on 2006-07-07
When the PKG_CONFIG_PATH is set correctly it should automatically adjust the -I parameters to point to the new path. Have you exported the PKG_CONFIG_PATH variable? Or maybe there's a typo in it? Works fine on my machine...

---

### Post by mlind on 2006-07-07
> **nagilum said:**
> When the PKG_CONFIG_PATH is set correctly it should automatically adjust the -I parameters to point to the new path. Have you exported the PKG_CONFIG_PATH variable? Or maybe there's a typo in it? Works fine on my machine...

Yes I have, exporting PKG_CONFIG_PATH makes 'configure' part work as expected, but 'make' throws errors about not finding glib headers.
I think the thing I've setup here is known as SYSROOT.

I'm not very familiar with this pkg-config stuff, if someone can help a bit it would be great.

---

### Post by nagilum on 2006-07-08
Hm.. strange. When I install glib to say /tmp/glib and set the PKG_CONFIG_PATH variable to /tmp/glib/lib/pkgconfig I get the following, as expected:
```

$ export PKG_CONFIG_PATH=/tmp/glib/lib/pkgconfig
$ pkg-config --libs --cflags glib-2.0
-I/tmp/glib/include/glib-2.0 -I/tmp/glib/lib/glib-2.0/include  -L/tmp/glib/lib -lglib-2.0

```
I used this several times and it always worked fine. Which application are you trying to compile with this setup?

---

### Post by mlind on 2006-07-08
> **nagilum said:**
> Hm.. strange. When I install glib to say /tmp/glib and set the PKG_CONFIG_PATH variable to /tmp/glib/lib/pkgconfig I get the following, as expected:
```

$ export PKG_CONFIG_PATH=/tmp/glib/lib/pkgconfig
$ pkg-config --libs --cflags glib-2.0
-I/tmp/glib/include/glib-2.0 -I/tmp/glib/lib/glib-2.0/include  -L/tmp/glib/lib -lglib-2.0

```
I used this several times and it always worked fine. Which application are you trying to compile with this setup?

Thanks for your response.

I think I'm doing something essentially wrong here..

When you install to non-standard location, you specify it using --prefix and paths related to that prefix. The problem is here that everything is installed on their normal locations on chroot environment, that's the main idea. But from outside, I would need /chroot/dapper-dev/ appended to each pkg-config path..

---

### Post by nagilum on 2006-07-08
> **mlind said:**
> When you install to non-standard location, you specify it using --prefix and paths related to that prefix. The problem is here that everything is installed on their normal locations on chroot environment, that's the main idea. But from outside, I would need /chroot/dapper-dev/ appended to each pkg-config path..

The --prefix is actually also used when packages are installed into the standard location, it's simply set to '/usr/local' instead of the non-standard place. Your setup should work fine with a prefix value of /chroot/dapper-dev/usr for example. Inside the chroot there's no need to use the PKG_CONFIG_PATH as everything is installed in locations which are searched by default. When mounting the chroot in another host system, as you did, PKG_CONFIG_PATH is actually the right way to go (aditionally you might want to adjust LD_LIBRARY_PATH and PATH).
I'm not sure why it doesn't work for you, but it actually should work.

---

### Post by mlind on 2006-07-08
> **nagilum said:**
> The --prefix is actually also used when packages are installed into the standard location, it's simply set to '/usr/local' instead of the non-standard place. Your setup should work fine with a prefix value of /chroot/dapper-dev/usr for example. Inside the chroot there's no need to use the PKG_CONFIG_PATH as everything is installed in locations which are searched by default. When mounting the chroot in another host system, as you did, PKG_CONFIG_PATH is actually the right way to go (aditionally you might want to adjust LD_LIBRARY_PATH and PATH).
I'm not sure why it doesn't work for you, but it actually should work.

I think I must investigage this problem a bit before giving any constructive answer :mrgreen: Thanks your help so far.

I reckon the problem is that some autotool is not generating path to jailed environment correctly. Stuff inside the jail works correctly and things compile there without any tweaking, it's just I don't want to compile anything in there, quite the opposite.

---

### Post by ravon on 2008-04-27
Sorry to revive such an old thread, but I'm kind of in the same boat.

My problem is that I don't know where the package will be installed since every developer will have a different directory layout and I want to be able to build once and deploy everywhere. The approach I took was to modify the ".pc" files before packaging, replacing the prefix line so it reads:
prefix=$${TOOLS}

TOOLS will then be exported by all our build scripts and --cflags will, for example, give "-I${TOOLS}/include". This works most of the time, but when configuring Xorg (libX11) it fails to expand the variable when testing for keysymdef.h. Everything else seems to work though.

Any ideas? I've tried to return basically everything, $TOOLS, $$TOOLS, ${TOOLS} and $${TOOLS} and switched the configure script from /bin/sh to /bin/bash, but for some reason it doesn't get expanded to the full path.

---

