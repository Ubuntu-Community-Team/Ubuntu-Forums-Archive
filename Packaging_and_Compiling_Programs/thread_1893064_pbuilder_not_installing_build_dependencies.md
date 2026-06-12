---
title: "pbuilder not installing build dependencies"
date: 2011-12-09
forum: Packaging and Compiling Programs
---

### Post by djsephiroth on 2011-12-09
[http://paste.ubuntu.com/764997/](http://paste.ubuntu.com/764997/)

```
 -> Attempting to satisfy build-dependencies
 -> Creating pbuilder-satisfydepends-dummy package
Package: pbuilder-satisfydepends-dummy
Version: 0.invalid.0
Architecture: i386
Maintainer: Debian Pbuilder Team <pbuilder-maint@lists.alioth.debian.org>
Description: Dummy package to satisfy dependencies with aptitude - created by pbuilder
 This package was created automatically by pbuilder to satisfy the
 build-dependencies of the package being currently built.
Depends: debhelper (>= 8.0.0), linux-headers-generic-pae
dpkg-deb: building package `pbuilder-satisfydepends-dummy' in `/tmp/satisfydepends-aptitude/pbuilder-satisfydepends-dummy.deb'.
Selecting previously unselected package pbuilder-satisfydepends-dummy.
(Reading database ... 16188 files and directories currently installed.)
Unpacking pbuilder-satisfydepends-dummy (from .../pbuilder-satisfydepends-dummy.deb) ...
dpkg: pbuilder-satisfydepends-dummy: dependency problems, but configuring anyway as you requested:
 pbuilder-satisfydepends-dummy depends on debhelper (>= 8.0.0); however:
  Package debhelper is not installed.
 pbuilder-satisfydepends-dummy depends on linux-headers-generic-pae; however:
  Package linux-headers-generic-pae is not installed.
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
                                 Depends: linux-headers-generic-pae which is a virtual package.
Unable to resolve dependencies!  Giving up...
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Abort.
 -> Finished parsing the build-deps
Reading package lists...
Building dependency tree...
Reading state information...
fakeroot is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 pbuilder-satisfydepends-dummy : Depends: debhelper (>= 8.0.0) but it is not installable
                                 Depends: linux-headers-generic-pae but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by djsephiroth on 2011-12-09
Solution: pbuilder-dist precise update

---

