---
title: "Error packaging python program"
date: 2013-01-25
forum: Packaging and Compiling Programs
---

### Post by JamesTheAwesomeDude on 2013-01-25
I asked to be the debian maintainer for a program called MCEdit. It's written in python.

I'm trying to package it up, but I keep getting this:
```
james@james-OptiPlex-GX620:~/sandbox/mcedit/mcedit-0.1.6$ debuild
 dpkg-buildpackage -rfakeroot -D -us -uc
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): -D_FORTIFY_SOURCE=2
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions -Wl,-z,relro
dpkg-buildpackage: source package mcedit
dpkg-buildpackage: source version 0.1.6-1
dpkg-buildpackage: source changed by James Edington <codegeek98@gmail.com>
 dpkg-source --before-build mcedit-0.1.6
dpkg-buildpackage: host architecture amd64
 fakeroot debian/rules clean
dh clean
   dh_testdir
   dh_auto_clean
   dh_clean
 dpkg-source -b mcedit-0.1.6
dpkg-source: info: using source format `3.0 (quilt)'
dpkg-source: info: building mcedit using existing ./mcedit_0.1.6.orig.tar.bz2
dpkg-source: info: building mcedit in mcedit_0.1.6-1.debian.tar.gz
dpkg-source: info: building mcedit in mcedit_0.1.6-1.dsc
 debian/rules build
dh build
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
 fakeroot debian/rules binary
dh binary
   dh_testroot
   dh_prep
   dh_installdirs
   dh_auto_install
   dh_install
cp: cannot stat `debian/tmp/build-stamp': No such file or directory
dh_install: cp -a debian/tmp/build-stamp debian/mcedit//usr/lib/mcedit/ returned exit code 1
make: *** [binary] Error 2
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2
debuild: fatal error at line 1350:
dpkg-buildpackage -rfakeroot -D -us -uc failed
james@james-OptiPlex-GX620:~/sandbox/mcedit/mcedit-0.1.6$ 
```
My rules file looks like this:
```
#!/usr/bin/make -f
%:
	dh $@
```
..and my install file looks like this: [http://pastebin.com/Qh62ngrb](http://pastebin.com/Qh62ngrb)

I have two questions: how do I fix this, and how do I compile for an "all" architecture. -ai386 is for 32-bit, but -aall doesn't work.

---

### Post by MadCow108 on 2013-01-26
what is "build-stamp" doing in the install file?

if its python package you should use:
dh $@ --with python2

don't install everything manually in the .install files, let the software's build system do that (in python case usually setup.py which is called automatically by dh_auto_*)
you only need to do it manually if the softwares buildsystem is broken, in which case ask the developers to fix it.

an arch all package is defined by the Architecture: tag in debian/control

---

### Post by JamesTheAwesomeDude on 2013-01-27
Aha. Thanks.

Everything's working now. :popcorn:

---

