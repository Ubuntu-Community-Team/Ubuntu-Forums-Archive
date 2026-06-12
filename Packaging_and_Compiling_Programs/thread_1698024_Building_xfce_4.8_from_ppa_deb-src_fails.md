---
title: "Building xfce 4.8 from ppa deb-src fails"
date: 2011-03-01
forum: Packaging and Compiling Programs
---

### Post by glennr on 2011-03-01
I want to install xfce 4.8 on an amd64 box running 10.04. There is a ppa ([https://launchpad.net/~alexx2000/+archive/xfce]("https://launchpad.net/~alexx2000/+archive/xfce"))  which has the only the 32 bit packages so I thought I'd build it from the deb-src packages supplied in the ppa.

When I try to build one of the packages ```
sudo apt-get --build source garcon
``` I get the error:
```

make[4]: Entering directory `/home/glenn/garcon-0.1.5/garcon'
  CC     libgarcon_1_la-garcon-config.lo
/bin/bash ../libtool --silent --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I.. -I.. -DGARCON_COMPILATION -DGARCON_VERSION_API=\"1\" -DG_LOG_DOMAIN=\"garcon\"    -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -fPIE  -fstack-protector  -D_FORTIFY_SOURCE=2  -Wformat -Wformat-security  -DNDEBUG -DG_DISABLE_CAST_CHECKS -c -o libgarcon_1_la-garcon-config.lo `test -f 'garcon-config.c' || echo './'`garcon-config.c
In file included from /usr/include/glib-2.0/glib/gbookmarkfile.h:28,
                 from /usr/include/glib-2.0/glib.h:39,
                 from /usr/include/glib-2.0/gobject/gtype.h:26,
                 from /usr/include/glib-2.0/gobject/gboxed.h:26,
                 from /usr/include/glib-2.0/glib-object.h:25,
                 from ../garcon/garcon-config.h:28,
                 from garcon-config.c:25:
/usr/include/time.h:226: error: expected declaration specifiers or '...' before '__locale_t'

```

This seems very odd, given that the error is coming from the system include file time.h. A previous attempt to build xfce 4.8 from source, following [http://ubuntuforums.org/showthread.php?t=1676774&page=2](http://ubuntuforums.org/showthread.php?t=1676774&page=2) resulted in a similar error in time.h.

Can someone suggest how to diagnose or fix this?

---

### Post by MadCow108 on 2011-03-02
I can't reproduce the build failure in my lucid pbuilder (32 and 64 bit).
Do you have any other ppa's activated?

---

### Post by glennr on 2011-03-02
I only have the ppa with the source, mentioned in my earlier post.

I have since discovered that there is a 64bit ppa (still a work in progress) [http://ppa.launchpad.net/neuromancer85/xfce48-lucid-ppa/ubuntu]("http://cs:3142/ppa.launchpad.net/neuromancer85/xfce48-lucid-ppa/ubuntu") and using that ppa I get the same error. Have also been unable to find any references to the error I am getting on the web.

Given that it works for you and others I suspect that my system is broken somehow. The machine has recently been updated from 8.04, and started out at 7.04 I think, so it probably has some cruft.

Any suggestions as to what might be broken?

---

### Post by glennr on 2011-03-02
Found the problem with my system. I had a version of gcc-4.3 in /usr/local/. Removed that and now it builds, but eventually fails with:
```

   dh_installdeb
   dh_gencontrol
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)

```

---

### Post by MadCow108 on 2011-03-02
this is expected as the package only declares to build for i386
add amd64 to all architecture entries in debian/control.
(maybe there is also an flag for debuild to enforce it, but I am unaware of one)

then it should build on that plattform (but may not work, depending if i386 only had a reason)

---

### Post by SoFl W on 2011-07-15
Were you able to get Xfce 4.8 working with 10.4 64bit?

---

