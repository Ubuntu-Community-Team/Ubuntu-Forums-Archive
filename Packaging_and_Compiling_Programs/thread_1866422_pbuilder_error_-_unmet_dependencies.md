---
title: "pbuilder error - unmet dependencies"
date: 2011-10-21
forum: Packaging and Compiling Programs
---

### Post by emeiri on 2011-10-21
Hi,

I'm trying to build a package using pbuilder and get the following error:

sudo pbuilder build ./assimp_2.0.863+dfsg-1.dsc
I: using fakeroot in build.
I: Current time: Fri Oct 21 17:28:00 IST 2011
I: pbuilder-time-stamp: 1319210880
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
Architecture: amd64
Maintainer: Debian Pbuilder Team <pbuilder-maint@lists.alioth.debian.org>
Description: Dummy package to satisfy dependencies with aptitude - created by pbuilder
 This package was created automatically by pbuilder to satisfy the
 build-dependencies of the package being currently built.
Depends: debhelper (>= 7.0.1), dh-buildinfo, devscripts (>= 2.10.7~), python (>= 2.6.5), cdbs (>= 0.4.95~), python-dev (>= 2.3.5-7), dpkg-dev (>= 1.15.6), pkg-kde-tools, cmake, libboost1.46-dev | libboost-dev, zlib1g-dev | libz-dev, doxygen
dpkg-deb: building package `pbuilder-satisfydepends-dummy' in `/tmp/satisfydepends-aptitude/pbuilder-satisfydepends-dummy.deb'.
Selecting previously deselected package pbuilder-satisfydepends-dummy.
(Reading database ... 13749 files and directories currently installed.)
Unpacking pbuilder-satisfydepends-dummy (from .../pbuilder-satisfydepends-dummy.deb) ...
dpkg: pbuilder-satisfydepends-dummy: dependency problems, but configuring anyway as you requested:
 pbuilder-satisfydepends-dummy depends on debhelper (>= 7.0.1); however:
  Package debhelper is not installed.
 pbuilder-satisfydepends-dummy depends on dh-buildinfo; however:
  Package dh-buildinfo is not installed.
 pbuilder-satisfydepends-dummy depends on devscripts (>= 2.10.7~); however:
  Package devscripts is not installed.
 pbuilder-satisfydepends-dummy depends on python (>= 2.6.5); however:
  Package python is not installed.
 pbuilder-satisfydepends-dummy depends on cdbs (>= 0.4.95~); however:
  Package cdbs is not installed.
 pbuilder-satisfydepends-dummy depends on python-dev (>= 2.3.5-7); however:
  Package python-dev is not installed.
 pbuilder-satisfydepends-dummy depends on pkg-kde-tools; however:
  Package pkg-kde-tools is not installed.
 pbuilder-satisfydepends-dummy depends on cmake; however:
  Package cmake is not installed.
 pbuilder-satisfydepends-dummy depends on libboost1.46-dev | libboost-dev; however:
  Package libboost1.46-dev is not installed.
  Package libboost-dev is not installed.
 pbuilder-satisfydepends-dummy depends on zlib1g-dev | libz-dev; however:
  Package zlib1g-dev is not installed.
  Package libz-dev is not installed.
 pbuilder-satisfydepends-dummy depends on doxygen; however:
  Package doxygen is not installed.
Setting up pbuilder-satisfydepends-dummy (0.invalid.0) ...
The following NEW packages will be installed:
  bsdmainutils{a} debhelper{a} devscripts{a} dh-buildinfo{a} file{a} gettext{a} gettext-base{a} groff-base{a} html2text{a} intltool-debian{a} libcroco3{a} libdb4.8{a} libexpat1{a} libmagic1{a} 
  libpipeline1{a} libunistring0{a} libxml2{a} man-db{a} mime-support{a} po-debconf{a} python{a} python2.7{a} 
The following packages are RECOMMENDED but will NOT be installed:
  at curl dctrl-tools dput dupload libjson-perl libmail-sendmail-perl libparse-debcontrol-perl liburi-perl libwww-perl lintian lynx-cur patchutils python-debian python-magic strace unzip wdiff wget wget 
  xml-core 
0 packages upgraded, 22 newly installed, 0 to remove and 0 not upgraded.
Need to get 9902 kB of archives. After unpacking 34.5 MB will be used.
The following packages have unmet dependencies:
  pbuilder-satisfydepends-dummy: Depends: cdbs (>= 0.4.95~) but it is not going to be installed.
                                 Depends: python-dev (>= 2.3.5-7) but it is not going to be installed.
                                 Depends: pkg-kde-tools but it is not going to be installed.
                                 Depends: cmake but it is not going to be installed.
                                 Depends: libboost1.46-dev but it is not going to be installed. or
                                          libboost-dev but it is not going to be installed.
                                 Depends: zlib1g-dev but it is not going to be installed. or
                                          libz-dev which is a virtual package.
                                 Depends: doxygen but it is not going to be installed.
Unable to resolve dependencies!  Giving up...
The following NEW packages will be installed:
  bsdmainutils{a} debhelper{a} devscripts{a} dh-buildinfo{a} file{a} gettext{a} gettext-base{a} groff-base{a} html2text{a} intltool-debian{a} libcroco3{a} libdb4.8{a} libexpat1{a} libmagic1{a} 
  libpipeline1{a} libunistring0{a} libxml2{a} man-db{a} mime-support{a} po-debconf{a} python{a} python2.7{a} 
The following packages are RECOMMENDED but will NOT be installed:
  at curl dctrl-tools dput dupload libjson-perl libmail-sendmail-perl libparse-debcontrol-perl liburi-perl libwww-perl lintian lynx-cur patchutils python-debian python-magic strace unzip wdiff wget wget 
  xml-core 
0 packages upgraded, 22 newly installed, 0 to remove and 0 not upgraded.
Need to get 9902 kB of archives. After unpacking 34.5 MB will be used.
Abort.
 -> Finished parsing the build-deps
Reading package lists...
Building dependency tree...
Reading state information...
fakeroot is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 pbuilder-satisfydepends-dummy : Depends: debhelper (>= 7.0.1) but it is not going to be installed
                                 Depends: dh-buildinfo but it is not going to be installed
                                 Depends: devscripts (>= 2.10.7~) but it is not going to be installed
                                 Depends: python (>= 2.6.5) but it is not going to be installed
                                 Depends: cdbs (>= 0.4.95~) but it is not going to be installed
                                 Depends: python-dev (>= 2.3.5-7) but it is not going to be installed
                                 Depends: pkg-kde-tools but it is not going to be installed
                                 Depends: cmake but it is not going to be installed
                                 Depends: libboost1.46-dev but it is not going to be installed or
                                          libboost-dev but it is not going to be installed
                                 Depends: zlib1g-dev but it is not going to be installed or
                                          libz-dev
                                 Depends: doxygen but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
I: Copying back the cached apt archive contents
I: unmounting /var/cache/pbuilder/ccache filesystem
I: unmounting dev/pts filesystem
I: unmounting proc filesystem
I: cleaning the build env 
I: removing directory /var/cache/pbuilder/build//22142 and its subdirectories

Looks like the setup is broken in some way. I ran 'apt-get -f install' on both my main env as well as the pbuilder one (using pbuilder --login) but there were no errors to fix.

I'm running 11.10 64 bits.

What should I do?

Thanks,

Etay

---

### Post by MadCow108 on 2011-10-22
I find pbuilders dependency output hard to decipher.
I usually log in and create a build dependency package with mk-build-deps.
Installing that with e.g gdebi will hopefully give you a better error message.

---

### Post by emeiri on 2011-10-22
Thanks.

Can you share a few more details how to do this?

I have devscripts installed both on my main env as well as inside the pbuilder env. How do I create the dependency package for the specific dsc which is failing?

Etay

---

### Post by emeiri on 2011-10-22
Problem solved. Turns out that the package I'm trying to build only exists on precise, so I had to upgrade my pbuilder environment using the following command:

sudo pbuilder update --distribution precise --override-config

After that I was able to build.

Thanks,

Etay

---

### Post by MadCow108 on 2011-10-22
for the record, using mk-build-deps:
```
cd package-dir
pbuilder --login --bindmounts=$PWD
cd package-dir
mk-build-deps
apt-get install gdebi-core
gdebi *build-deps.deb

```

you can probably also use
```
PBUILDERSATISFYDEPENDSCMD="/usr/lib/pbuilder/pbuilder-satisfydepends-gdebi"
```
in .pbuilderrc to get the same effect

---

