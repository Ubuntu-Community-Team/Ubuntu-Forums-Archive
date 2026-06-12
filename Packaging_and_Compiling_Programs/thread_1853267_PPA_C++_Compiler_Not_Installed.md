---
title: "PPA: C++ Compiler Not Installed?"
date: 2011-10-01
forum: Packaging and Compiling Programs
---

### Post by Gias Kay on 2011-10-01
Was trying to build a package on PPA, and got this error returned:

```
Checking whether the C++ compiler worksno
c++ compiler not installed!
make: *** [debian/stamp-scons-build] Error 1
dpkg-buildpackage: error: debian/rules build gave error exit status 2
```

[[COLOR="DeepSkyBlue"](Buildlog)[/COLOR]]("https://launchpad.net/~gias-kay-lee/+archive/mongodb/+build/2817090")

Thought it's something about Build-Depends, so I added g++ into build dependencies, but the same error still occured:

```
g++: already installed (4:4.4.4-1ubuntu2)
```
```
Checking whether the C++ compiler worksno
c++ compiler not installed!
make: *** [debian/stamp-scons-build] Error 1
dpkg-buildpackage: error: debian/rules build gave error exit status 2
```

[[COLOR="DeepSkyBlue"](Buildlog)[/COLOR]]("https://launchpad.net/~gias-kay-lee/+archive/mongodb-test/+build/2816894")

Tarballs were taken from Debian Sid: [http://packages.debian.org/sid/mongodb](http://packages.debian.org/sid/mongodb)

Not sure where the source of the error is. I was building for Maverick. Anyone got any ideas? Thanks!

---

