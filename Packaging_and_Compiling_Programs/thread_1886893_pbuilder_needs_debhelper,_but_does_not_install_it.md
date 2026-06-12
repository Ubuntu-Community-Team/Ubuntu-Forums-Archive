---
title: "pbuilder needs debhelper, but does not install it"
date: 2011-11-25
forum: Packaging and Compiling Programs
---

### Post by djsephiroth on 2011-11-25
Trying to build a package using pbuilder-dist. I'm on Xubuntu
Oneiric; target is vanilla Oneiric server.
 
Error:
```
dpkg: pbuilder-satisfydepends-dummy: dependency problems, but configuring anyway as you requested:
 pbuilder-satisfydepends-dummy depends on debhelper (>= 8.0.0); however:
  Package debhelper is not installed.

```

---

### Post by SevenMachines on 2011-11-26
Do you have it mentioned in debian/control ? Something like 
```
Build-Depends: debhelper (>= 8)
```

---

### Post by djsephiroth on 2011-11-28
Yes, that exact version in fact.

```
Build-Depends: debhelper (>= 8.0.0), build-essential, linux-headers-generic-pae
```

---

### Post by djsephiroth on 2011-11-28
If I log into the pbuilder chroot instead of doing a "pbuilder-dist oneiric build", I can install debhelper 8.9.0ubuntu1 in the chroot. 

Mystified as to what's going on.

---

### Post by SevenMachines on 2011-11-28
Does it look something like
```
Unpacking pbuilder-satisfydepends-dummy (from .../pbuilder-satisfydepends-dummy.deb) ...
dpkg: pbuilder-satisfydepends-dummy: dependency problems, but configuring anyway as you requested:
 pbuilder-satisfydepends-dummy depends on debhelper (>= 8); however:
  Package debhelper is not installed.
Setting up pbuilder-satisfydepends-dummy (0.invalid.0) ...
Reading package lists...
Building dependency tree...
Reading state information...
Initializing package states...
Writing extended state information...
The following NEW packages will be installed:
  bsdmainutils{a} debhelper{a} file{a} gettext{a} gettext-base{a} 
  groff-base{a} html2text{a} intltool-debian{a} libcroco3{a} libmagic1{a} 
  libpipeline1{a} libunistring0{a} libxml2{a} man-db{a} po-debconf{a} 
0 packages upgraded, 15 newly installed, 0 to remove and 0 not upgraded.
Need to get 5675 kB of archives. After unpacking 19.1 MB will be used.

```All that means is that pbuilder-satisfydepends-dummy is being installed before its debhelper dependency, which is fine because debhelper is being downloaded and installed right after it.

I think I misunderstood your initial question, if it looks like above then this is absolutely normal and not going to cause any issues with whatever you're building

---

### Post by djsephiroth on 2011-11-28
Here's the output:

```

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
Depends: debhelper (>= 8.0.0)
dpkg-deb: building package `pbuilder-satisfydepends-dummy' in `/tmp/satisfydepends-aptitude/pbuilder-satisfydepends-dummy.deb'.
Selecting previously deselected package pbuilder-satisfydepends-dummy.
(Reading database ... 16071 files and directories currently installed.)
Unpacking pbuilder-satisfydepends-dummy (from .../pbuilder-satisfydepends-dummy.deb) ...
dpkg: pbuilder-satisfydepends-dummy: dependency problems, but configuring anyway as you requested:
 pbuilder-satisfydepends-dummy depends on debhelper (>= 8.0.0); however:
  Package debhelper is not installed.
Setting up pbuilder-satisfydepends-dummy (0.invalid.0) ...
Reading package lists...
Building dependency tree...
Reading state information...
Initializing package states...
Writing extended state information...
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
The following packages have unmet dependencies:
  pbuilder-satisfydepends-dummy: Depends: debhelper (>= 8.0.0) which is a virtual package.
Unable to resolve dependencies!  Giving up...
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Abort.
 -> Finished parsing the build-deps
Reading package lists...
Building dependency tree...
Reading state information...
Package bash-completion is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  bash

Package debhelper is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

```

---

### Post by djsephiroth on 2011-11-28
I'm able to resolve the issue by giving pbuilder the "--save-after-exec" option and manually installing debhelper. However, the root cause is still mysterious to me, so I'd like to figure it out. Thanks for the help.

---

### Post by SevenMachines on 2011-11-28
Does seem a bit strange, have you run update recently? Or do you get the same error if you newly create the base archive

---

### Post by djsephiroth on 2011-11-28
Updated several times, so that's ruled out. 

I have nuked that chroot from orbit and created a new one. So far so good. Still mysterious as to the root cause, but at least it's working. Thanks for the help!

---

