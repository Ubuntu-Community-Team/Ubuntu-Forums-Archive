---
title: "[SOLVED] Need help pbuilding a hello world app with unpackaged library"
date: 2009-01-09
forum: Packaging and Compiling Programs
---

### Post by KIAaze on 2009-01-09
Hi,

I'm trying to package a simple hello world app using an external library called "greetings".

To do this, I'm trying to use a local apt repository as indicated here: [http://www.netfort.gr.jp/~dancer/software/pbuilder-doc/pbuilder-doc.html#usingspecialaptsources](http://www.netfort.gr.jp/~dancer/software/pbuilder-doc/pbuilder-doc.html#usingspecialaptsources)

I attached the hello + greetings sources I used. (You may also find them useful if you're trying to learn how to use autotools. ;) )

The "greetings" library is static, but I don't think that should make a big difference since it is listed as a "Build-Depends" in debian/control for "hello".

**_Setup:_**

/var/cache/pbuilder/hook.d/D10locapt:
```

# cat /var/cache/pbuilder/hooks/D70results
#!/bin/bash
set -x
cd /var/cache/pbuilder/result/
/usr/bin/dpkg-scanpackages . /dev/null | gzip -9c > /var/cache/pbuilder/result/Packages.gz
/usr/bin/dpkg-scansources . /dev/null | gzip -9c > /var/cache/pbuilder/result/Sources.gz

#/usr/bin/dpkg-scansources . /dev/null > /var/cache/pbuilder/result/Packages
#/usr/bin/dpkg-scanpackages . /dev/null > /var/cache/pbuilder/result/Packages
/usr/bin/apt-get update


```

~/.pbuilderrc:
```

HOOKDIR="/var/cache/pbuilder/hook.d"
BINDMOUNTS="/var/cache/pbuilder/result"

```

_**What I did:**_

1)pbuild the library
```
cd greetings-1.0
debuild
debuild -S
sudo pbuilder build ../greetings_1.0.dsc

```
No problem here.

2)Installing lib locally to be able to build hello:
```
./configure && make && sudo make install
cd ..

```

3)pbuild hello
```
cd hello-1.0
debuild
debuild -S
sudo pbuilder  build ../hello_1.0.dsc --othermirror "deb file:/var/cache/pbuilder/result/ /"

```
Building fails with the following output:
```

I: using fakeroot in build.
Current time: Fri Jan  9 15:01:02 CET 2009
pbuilder-time-stamp: 1231509662
Building the build Environment
 -> extracting base tarball [/var/cache/pbuilder/base.tgz]
 -> creating local configuration
 -> copying local configuration
 -> mounting /proc filesystem
 -> mounting /dev/pts filesystem
-> Mounting /var/cache/pbuilder/result
 -> policy-rc.d already exists
Obtaining the cached apt archive contents
Installing the build-deps
+ cd /var/cache/pbuilder/result/
+ /usr/bin/dpkg-scanpackages . /dev/null
+ gzip -9c
 ** Packages in archive but missing from override file: **
  greetings 

 Wrote 4 entries to output Packages file.
+ /usr/bin/dpkg-scansources . /dev/null
+ gzip -9c
+ /usr/bin/apt-get update
Hit http://de.archive.ubuntu.com intrepid Release.gpg
Hit http://de.archive.ubuntu.com intrepid Release
Hit http://de.archive.ubuntu.com intrepid/main Packages
Hit http://de.archive.ubuntu.com intrepid/restricted Packages
Hit http://de.archive.ubuntu.com intrepid/universe Packages
Hit http://de.archive.ubuntu.com intrepid/multiverse Packages
Reading package lists...
 -> user script /var/cache/pbuilder/build//1932/tmp/hooks/D10locapt finished
W: skipping an editor backup file /var/cache/pbuilder/build//1932/tmp/hooks/D10locapt~
 -> Attempting to satisfy build-dependencies
 -> Creating pbuilder-satisfydepends-dummy package
Package: pbuilder-satisfydepends-dummy
Version: 0.invalid.0
Architecture: i386
Maintainer: Debian Pbuilder Team <pbuilder-maint@lists.alioth.debian.org>
Description: Dummy package to satisfy dependencies with aptitude - created by pbuilder
 This package was created automatically by pbuilder and should
Depends: debhelper (>= 7), autotools-dev, greetings
dpkg-deb: building package `pbuilder-satisfydepends-dummy' in `/tmp/satisfydepends-aptitude/pbuilder-satisfydepends-dummy.deb'.
Reading package lists...
Building dependency tree...
Reading state information...
aptitude is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Selecting previously deselected package pbuilder-satisfydepends-dummy.
(Reading database ... 12763 files and directories currently installed.)
Unpacking pbuilder-satisfydepends-dummy (from .../pbuilder-satisfydepends-dummy.deb) ...
dpkg: dependency problems prevent configuration of pbuilder-satisfydepends-dummy:
 pbuilder-satisfydepends-dummy depends on debhelper (>= 7); however:
  Package debhelper is not installed.
 pbuilder-satisfydepends-dummy depends on autotools-dev; however:
  Package autotools-dev is not installed.
 pbuilder-satisfydepends-dummy depends on greetings; however:
  Package greetings is not installed.
dpkg: error processing pbuilder-satisfydepends-dummy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pbuilder-satisfydepends-dummy
Reading package lists...
Building dependency tree...
Reading state information...
Initializing package states...
Writing extended state information...
The following packages are BROKEN:
  pbuilder-satisfydepends-dummy 
The following NEW packages will be installed:
  autotools-dev{a} bsdmainutils{a} debhelper{a} gettext{a} gettext-base{a} 
  groff-base{a} html2text{a} intltool-debian{a} man-db{a} po-debconf{a} 
0 packages upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4964kB of archives. After unpacking 17.2MB will be used.
The following packages have unmet dependencies:
  pbuilder-satisfydepends-dummy: Depends: greetings which is a virtual package.
The following actions will resolve these dependencies:

Remove the following packages:
pbuilder-satisfydepends-dummy

Score is -9850

Writing extended state information...
(Reading database ... 12763 files and directories currently installed.)
Removing pbuilder-satisfydepends-dummy ...
Selecting previously deselected package bsdmainutils.
(Reading database ... 12763 files and directories currently installed.)
Unpacking bsdmainutils (from .../bsdmainutils_6.1.10ubuntu2_i386.deb) ...
Setting up bsdmainutils (6.1.10ubuntu2) ...

Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Writing extended state information...
Aptitude couldn't satisfy the build dependencies
E: pbuilder-satisfydepends failed.
Copying back the cached apt archive contents
 -> unmounting /var/cache/pbuilder/result filesystem
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> cleaning the build env 
    -> removing directory /var/cache/pbuilder/build//1932 and its subdirectories

```

Any ideas?

Note: To test the local apt, I added:
```
deb file:/var/cache/pbuilder/result/ /
```
to /etc/apt/sources.lst and it worked.
Why doesn't it work in pbuilder?

P.S:
I'm planning to package another app that way (app+lib). But since pbuilder is slow, I'm testing with a simple hello world app first. ;)

---

### Post by KIAaze on 2009-01-09
Solved after reading the [man page]("http://www.linuxcertif.com/man/8/pbuilder/") a bit more. :)

> --override-config

    Specify to use different apt set up inside the chroot than it was used for creating the base.tgz. Specify this when you want to do pbuilder --update with a different distribution target set up.

   [B] --distribution, --mirror, --othermirror
     options are only valid when --override-config option is specified in --update target, or when pbuilder --create is being called.[/B]


So all I had to do (additionally to the above steps), was:
```
sudo pbuilder update --override-config --othermirror "deb file:/var/cache/pbuilder/result/ /"
sudo pbuilder build ../hello_1.0.dsc

```

Instead of using --othermirror, you can also add the following to your ~/.pbuilderrc:
```
OTHERMIRROR="deb file:/var/cache/pbuilder/result/ /"
```

Example ~/.pbuilderrc file:
```
HOOKDIR="/var/cache/pbuilder/hook.d"
BINDMOUNTS="/var/cache/pbuilder/result"
COMPONENTS="main restricted universe multiverse"
OTHERMIRROR="deb file:/var/cache/pbuilder/result/ /"

```

---

