---
title: "pbuilder-dist denied permission to /lib/"
date: 2011-11-28
forum: Packaging and Compiling Programs
---

### Post by djsephiroth on 2011-11-28
Building a kernel extension with pbuilder.

Input
```
pbuilder-dist oneiric build ../foo.dsc
```

Output
```
make[1]: Entering directory `/tmp/buildd/foo-4.28'
--- Making sure the 'misc' module directory exists...
test -d /lib/modules/3.0.0-12-generic-pae/misc || mkdir /lib/modules/3.0.0-12-generic-pae/misc
mkdir: cannot create directory `/lib/modules/3.0.0-12-generic-pae/misc': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/tmp/buildd/foo-4.28'
dh_auto_install: make -j1 install DESTDIR=/tmp/buildd/foo-4.28/debian/tmp returned exit code 2
make: *** [binary] Error 29
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2
E: Failed autobuilding of package

```

Pbuilder is not asking for my sudo password.

---

