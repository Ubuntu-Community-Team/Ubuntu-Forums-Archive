---
title: "Help Compiling a Program"
date: 2007-03-23
forum: Programming Talk
---

### Post by esaym on 2007-03-23
I am trying to make a deb of the lastest version of soundkonverter.  I am just doing it pretty much for fun.  Yea I know I could just update to fiesty and I would have the lastest stuff but I want to try to hold off updating until kde4.  Plus that gives me a good excuse to compile my own programs :D

Anyway the lucky program today is soundkonverter.  I followed: [http://www.ubuntuforums.org/showthread.php?t=51003](http://www.ubuntuforums.org/showthread.php?t=51003) because I want to make a deb.  After doing a ```
dpkg-buildpackage -rfakeroot
``` It stops with this error: 

```
/home/soundkonverter-0.3.2/soundkonverter-0.3.2/admin/missing: line 52: automake-1.9: command not found
WARNING: `automake-1.9' is missing on your system.  You should only need it if
         you modified `Makefile.am', `acinclude.m4' or `configure.in'.
         You might want to install the `Automake' and `Perl' packages.
         Grab them from any GNU archive site.
 cd . && perl admin/am_edit
cd . && perl admin/am_edit Makefile.in
cd . && rm -f configure
cd . && /usr/bin/make -f admin/Makefile.common configure
make[2]: Entering directory `/home/soundkonverter-0.3.2/soundkonverter-0.3.2'
configure.in:43: error: possibly undefined macro: AM_INIT_AUTOMAKE
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.in:48: error: possibly undefined macro: AM_CONFIG_HEADER
configure.in:51: error: possibly undefined macro: AC_CHECK_COMPILERS
configure.in:52: error: possibly undefined macro: AC_ENABLE_SHARED
configure.in:53: error: possibly undefined macro: AC_ENABLE_STATIC
configure.in:58: error: possibly undefined macro: AM_KDE_WITH_NLS
configure.in:61: error: possibly undefined macro: AC_PATH_KDE
configure.in:70: error: possibly undefined macro: AC_CHECK_KDEMAXPATHLEN
configure.in:204: error: possibly undefined macro: AM_CONDITIONAL
make[2]: *** [configure] Error 1
make[2]: Leaving directory `/home/soundkonverter-0.3.2/soundkonverter-0.3.2'
make[1]: *** [configure] Error 2
make[1]: Leaving directory `/home/soundkonverter-0.3.2/soundkonverter-0.3.2'
make: *** [build-stamp] Error 2
userdev@userdev-desktop:/home/soundkonverter-0.3.2/soundkonverter-0.3.2$
```

Files in question [configure]("http://lindsay.ath.cx/stuff/dev/configure") [configure.in]("http://lindsay.ath.cx/stuff/dev/configure.in") [configure.in.in]("http://lindsay.ath.cx/stuff/dev/configure.in.in")

Someone on irc told me that the am_init_automake command is actually deprecated.  If this is the problem is there anyway to automatically update the commands?

I always hate asking dev questions.  Seems like no one can ever answer my question.  I feel like I am so close to getting this deb built though.  I just gotta get it to work! :KS

---

### Post by Mr. C. on 2007-03-23
```
apt-get install automake
```

if you need 1.9 specifically:

```
apt-get install automake1.9
```

MrC

---

### Post by esaym on 2007-03-24
> **Mr. C. said:**
> ```
apt-get install automake
```

if you need 1.9 specifically:

```
apt-get install automake1.9
```

MrC


Ohh I forgot to mention.  I have installed automake 1.4-1.9.  None of them seemed to make any difference.  I only had one at a time installed too, not sure if that is the right way or not..

---

