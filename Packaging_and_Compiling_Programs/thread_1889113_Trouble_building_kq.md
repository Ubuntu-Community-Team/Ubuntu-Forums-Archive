---
title: "Trouble building kq"
date: 2011-11-30
forum: Packaging and Compiling Programs
---

### Post by dawynn on 2011-11-30
I was trying to upgrade the kq deb.  (kq was a game package that has been removed from Debian / Ubuntu because of lack of interest from original maintainers)  I was able to build everything using debuild, with only a couple lintian warnings, but now having issues with pbuilder.

Using a fully updated "precise" system.

Can someone help me understand why actual packages are being tagged as virtual packages?  And how to get pbuilder to download these packages?

Output from "sudo pbuilder build kq_0.99.cvs20091214-0ubuntu1.dsc":
```

I: using fakeroot in build.
I: Current time: Wed Nov 30 15:56:01 CST 2011
I: pbuilder-time-stamp: 1322690161
I: Building the build Environment
I: extracting base tarball [/var/cache/pbuilder/base.tgz]
I: creating local configuration
I: copying local configuration
I: mounting /proc filesystem
I: mounting /dev/pts filesystem
I: Mounting /var/cache/pbuilder/ccache
I: policy-rc.d already exists
I: Obtaining the cached apt archive contents
I: Setting up ccache
I: Installing the build-deps
 -> Attempting to satisfy build-dependencies
 -> Creating pbuilder-satisfydepends-dummy package
Package: pbuilder-satisfydepends-dummy
Version: 0.invalid.0
Architecture: i386
Maintainer: Debian Pbuilder Team <pbuilder-maint@lists.alioth.debian.org>
Description: Dummy package to satisfy dependencies with aptitude - created by pbuilder
 This package was created automatically by pbuilder to satisfy the
 build-dependencies of the package being currently built.
Depends: debhelper (>= 8.0), quilt, liballegro4.2-dev (>= 2:4.2.2-3), libaldmb1-dev, liblua50-dev, lua50, liblualib50-dev
dpkg-deb: building package `pbuilder-satisfydepends-dummy' in `/tmp/satisfydepends-aptitude/pbuilder-satisfydepends-dummy.deb'.
Selecting previously unselected package pbuilder-satisfydepends-dummy.
(Reading database ... 13877 files and directories currently installed.)
Unpacking pbuilder-satisfydepends-dummy (from .../pbuilder-satisfydepends-dummy.deb) ...
dpkg: pbuilder-satisfydepends-dummy: dependency problems, but configuring anyway as you requested:
 pbuilder-satisfydepends-dummy depends on debhelper (>= 8.0); however:
  Package debhelper is not installed.
 pbuilder-satisfydepends-dummy depends on quilt; however:
  Package quilt is not installed.
 pbuilder-satisfydepends-dummy depends on liballegro4.2-dev (>= 2:4.2.2-3); however:
  Package liballegro4.2-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libaldmb1-dev; however:
  Package libaldmb1-dev is not installed.
 pbuilder-satisfydepends-dummy depends on liblua50-dev; however:
  Package liblua50-dev is not installed.
 pbuilder-satisfydepends-dummy depends on lua50; however:
  Package lua50 is not installed.
 pbuilder-satisfydepends-dummy depends on liblualib50-dev; however:
  Package liblualib50-dev is not installed.
Setting up pbuilder-satisfydepends-dummy (0.invalid.0) ...
The following NEW packages will be installed:
  bsdmainutils{a} debhelper{a} diffstat{a} file{a} gettext{a} 
  gettext-base{a} groff-base{a} html2text{a} intltool-debian{a} 
  libcroco3{a} libgettextpo0{a} libmagic1{a} libpipeline1{a} 
  libunistring0{a} libxml2{a} man-db{a} po-debconf{a} quilt{a} 
The following packages are RECOMMENDED but will NOT be installed:
  curl libmail-sendmail-perl lynx-cur wget xml-core 
0 packages upgraded, 18 newly installed, 0 to remove and 0 not upgraded.
Need to get 300 kB/5817 kB of archives. After unpacking 18.8 MB will be used.
The following packages have unmet dependencies:
  pbuilder-satisfydepends-dummy: Depends: liballegro4.2-dev (>= 2:4.2.2-3) which is a virtual package.
                                 Depends: libaldmb1-dev which is a virtual package.
                                 Depends: liblua50-dev which is a virtual package.
                                 Depends: lua50 which is a virtual package.
                                 Depends: liblualib50-dev which is a virtual package.
Unable to resolve dependencies!  Giving up...
The following NEW packages will be installed:
  bsdmainutils{a} debhelper{a} diffstat{a} file{a} gettext{a} 
  gettext-base{a} groff-base{a} html2text{a} intltool-debian{a} 
  libcroco3{a} libgettextpo0{a} libmagic1{a} libpipeline1{a} 
  libunistring0{a} libxml2{a} man-db{a} po-debconf{a} quilt{a} 
The following packages are RECOMMENDED but will NOT be installed:
  curl libmail-sendmail-perl lynx-cur wget xml-core 
0 packages upgraded, 18 newly installed, 0 to remove and 0 not upgraded.
Need to get 300 kB/5817 kB of archives. After unpacking 18.8 MB will be used.
Abort.
 -> Finished parsing the build-deps
Reading package lists...
Building dependency tree...
Reading state information...
fakeroot is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 pbuilder-satisfydepends-dummy : Depends: debhelper (>= 8.0) but it is not going to be installed
                                 Depends: quilt but it is not going to be installed
                                 Depends: liballegro4.2-dev (>= 2:4.2.2-3) but it is not installable
                                 Depends: libaldmb1-dev but it is not installable
                                 Depends: liblua50-dev but it is not installable
                                 Depends: lua50 but it is not installable
                                 Depends: liblualib50-dev but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
I: Copying back the cached apt archive contents
I: unmounting /var/cache/pbuilder/ccache filesystem
I: unmounting dev/pts filesystem
I: unmounting proc filesystem

```

---

### Post by Bachstelze on 2011-11-30
Paste your .pbuilderrc. In particular, do you have universe enabled in pbuilder?

---

### Post by dawynn on 2011-11-30
Thank you so much!  That was enough of a hint.  Had to add this line:
COMPONENTS="main restricted universe multiverse"

---

