---
title: "pbuilder problems"
date: 2008-03-25
forum: Packaging and Compiling Programs
---

### Post by vixinu on 2008-03-25
Hi, I'm having a problem with pbuilder.  When I used it, I got this response (sorry it's long, I'm including it all because I don't know what's wrong.)
```
W: /home/jjacobs/.pbuilderrc does not exist
I: using fakeroot in build.
Current time: Tue Mar 25 16:39:30 EDT 2008
pbuilder-time-stamp: 1206477570
Building the build Environment
 -> extracting base tarball [/var/cache/pbuilder/base.tgz]
 -> creating local configuration
 -> copying local configuration
 -> mounting /proc filesystem
 -> mounting /dev/pts filesystem
 -> policy-rc.d already exists
Obtaining the cached apt archive contents
Installing the build-deps
 -> Attempting to satisfy build-dependencies
 -> Creating pbuilder-satisfydepends-dummy package
Package: pbuilder-satisfydepends-dummy
Version: 0.invalid.0
Architecture: powerpc
Maintainer: Debian Pbuilder Team <pbuilder-maint@lists.alioth.debian.org>
Description: Dummy package to satisfy dependencies with aptitude - created by pbuilder
 This package was created automatically by pbuilder and should
Depends: debhelper (>= 5)
dpkg-deb: building package `pbuilder-satisfydepends-dummy' in `/tmp/satisfydepends-aptitude/pbuilder-satisfydepends-dummy.deb'.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
aptitude is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Selecting previously deselected package pbuilder-satisfydepends-dummy.
(Reading database ... 9310 files and directories currently installed.)
Unpacking pbuilder-satisfydepends-dummy (from .../pbuilder-satisfydepends-dummy.deb) ...
dpkg: dependency problems prevent configuration of pbuilder-satisfydepends-dummy:
 pbuilder-satisfydepends-dummy depends on debhelper (>= 5); however:
  Package debhelper is not installed.
dpkg: error processing pbuilder-satisfydepends-dummy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pbuilder-satisfydepends-dummy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following NEW packages will be automatically installed:
  debhelper file gettext gettext-base html2text intltool-debian libmagic1 
  po-debconf 
The following NEW packages will be installed:
  debhelper file gettext gettext-base html2text intltool-debian libmagic1 
  po-debconf 
The following partially installed packages will be configured:
  pbuilder-satisfydepends-dummy 
0 packages upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3437kB of archives. After unpacking 13.6MB will be used.
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  debhelper intltool-debian po-debconf gettext file gettext-base html2text 
  libmagic1 

*** WARNING ***   Ignoring these trust violations because
                  aptitude::CmdLine::Ignore-Trust-Violations is 'true'!
Writing extended state information... Done
debconf: delaying package configuration, since apt-utils is not installed
Selecting previously deselected package libmagic1.
(Reading database ... 9310 files and directories currently installed.)
Unpacking libmagic1 (from .../libmagic1_4.21-3_powerpc.deb) ...
Selecting previously deselected package file.
Unpacking file (from .../file_4.21-3_powerpc.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-3build1_powerpc.deb) ...
Selecting previously deselected package gettext-base.
Unpacking gettext-base (from .../gettext-base_0.17-2ubuntu1_powerpc.deb) ...
Selecting previously deselected package gettext.
Unpacking gettext (from .../gettext_0.17-2ubuntu1_powerpc.deb) ...
Selecting previously deselected package intltool-debian.
Unpacking intltool-debian (from .../intltool-debian_0.35.0+20060710.1_all.deb) ...
Selecting previously deselected package po-debconf.
Unpacking po-debconf (from .../po-debconf_1.0.10_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_6.0.4ubuntu1_all.deb) ...
Setting up libmagic1 (4.21-3) ...

Setting up file (4.21-3) ...
Setting up html2text (1.3.2a-3build1) ...

Setting up gettext-base (0.17-2ubuntu1) ...

Setting up gettext (0.17-2ubuntu1) ...

Setting up intltool-debian (0.35.0+20060710.1) ...
Setting up po-debconf (1.0.10) ...

Setting up debhelper (6.0.4ubuntu1) ...
Setting up pbuilder-satisfydepends-dummy (0.invalid.0) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
 -> Finished parsing the build-deps
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  fakeroot
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/131kB of archives.
After this operation, 537kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  fakeroot
debconf: delaying package configuration, since apt-utils is not installed
Selecting previously deselected package fakeroot.
(Reading database ... 9921 files and directories currently installed.)
Unpacking fakeroot (from .../fakeroot_1.9ubuntu1_powerpc.deb) ...
Setting up fakeroot (1.9ubuntu1) ...

Copying back the cached apt archive contents
Copying source file
    -> copying [gmobilemedia-debhelper_0.4-1.dsc]
    -> copying [./gmobilemedia-debhelper_0.4.orig.tar.gz]
    -> copying [./gmobilemedia-debhelper_0.4-1.diff.gz]
Extracting source
dpkg-source: warning: could not verify signature on ./gmobilemedia-debhelper_0.4-1.dsc since gpg isn't installed
dpkg-source: extracting gmobilemedia-debhelper in gmobilemedia-debhelper-0.4
dpkg-source: unpacking gmobilemedia-debhelper_0.4.orig.tar.gz
dpkg-source: applying ./gmobilemedia-debhelper_0.4-1.diff.gz
 -> Building the package
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package gmobilemedia-debhelper
dpkg-buildpackage: source version 0.4-1
dpkg-buildpackage: source changed by Joshua Jacobs <vixinu@sbcglobal.net>
dpkg-buildpackage: host architecture powerpc
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean
make[1]: Entering directory `/tmp/buildd/gmobilemedia-debhelper-0.4'
make[1]: *** No rule to make target `clean'.  Stop.
make[1]: Leaving directory `/tmp/buildd/gmobilemedia-debhelper-0.4'
make: [clean] Error 2 (ignored)
dh_clean 
 dpkg-source -b gmobilemedia-debhelper-0.4
dpkg-source: building gmobilemedia-debhelper using existing gmobilemedia-debhelper_0.4.orig.tar.gz
dpkg-source: building gmobilemedia-debhelper in gmobilemedia-debhelper_0.4-1.diff.gz
dpkg-source: building gmobilemedia-debhelper in gmobilemedia-debhelper_0.4-1.dsc
 debian/rules build
dh_testdir
# Add here commands to configure the package.
touch configure-stamp
dh_testdir
# Add here commands to compile the package.
/usr/bin/make
make[1]: Entering directory `/tmp/buildd/gmobilemedia-debhelper-0.4'
make[1]: *** No targets specified and no makefile found.  Stop.
make[1]: Leaving directory `/tmp/buildd/gmobilemedia-debhelper-0.4'
make: *** [build-stamp] Error 2
dpkg-buildpackage: failure: debian/rules build gave error exit status 2
pbuilder: Failed autobuilding of package
 -> Aborting with an error
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> cleaning the build env 
    -> removing directory /var/cache/pbuilder/build//11377 and its subdirectories
```

---

### Post by mssever on 2008-03-26
It appears that there's a problem with the package you're trying to build. debian/rules exited with a status of 2, the error says. So there's an error there. You'll have to look through debian/rules and figure out what the bug is.

---

### Post by Vorian on 2008-03-26
```
make[1]: Entering directory `/tmp/buildd/gmobilemedia-debhelper-0.4'
make[1]: *** No targets specified and no makefile found.  Stop.

```

This is where your problem is.  You need to tell pbuilder what to do on this step in your debian/rules file.

---

