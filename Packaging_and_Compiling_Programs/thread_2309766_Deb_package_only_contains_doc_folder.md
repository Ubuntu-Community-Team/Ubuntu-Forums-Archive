---
title: "Deb package only contains doc folder"
date: 2016-01-13
forum: Packaging and Compiling Programs
---

### Post by lads on 2016-01-13
I am trying to package a useful programme that is presently only available from source. I am following the [packaging guide]("http://packaging.ubuntu.com/html/packaging-new-software.html") and all goes pretty smooth up to the creation of the *.deb* file. However, this file contains only the */doc* folder, as in this example:
```

$ lesspipe myprogramme_0.8.2-alpha1-0ubuntu1_amd64.deb
myprogramme_0.8.2-alpha1-0ubuntu1_amd64.deb:
 new debian package, version 2.0.
 size 3894 bytes: control archive=662 bytes.
     614 bytes,    10 lines      control              
     214 bytes,     3 lines      md5sums              
 Package: myprogramme
 Version: 0.8.2-alpha1-0ubuntu1
 Architecture: amd64
 Maintainer: luis-a-de-sousa <me@mail.com>
 Installed-Size: 30
 Section: unknown
 Priority: optional
 Homepage: http://www.myprogramme.com
 Description: A programme.
  A long description.

*** Contents:
drwxr-xr-x root/root         0 2016-01-12 11:21 ./
drwxr-xr-x root/root         0 2016-01-12 11:21 ./usr/
drwxr-xr-x root/root         0 2016-01-12 11:21 ./usr/share/
drwxr-xr-x root/root         0 2016-01-12 11:21 ./usr/share/doc/
drwxr-xr-x root/root         0 2016-01-12 11:21 ./usr/share/doc/myprogramme/
-rw-r--r-- root/root      3990 2016-01-12 10:58 ./usr/share/doc/myprogramme/README.md
-rw-r--r-- root/root       195 2016-01-12 11:02 ./usr/share/doc/myprogramme/changelog.Debian.gz
-rw-r--r-- root/root      1899 2016-01-12 11:14 ./usr/share/doc/myprogramme/copyright
```

What am I exactly missing here? Why aren't the build files being included in the *.deb*?

Thanks.

---

### Post by lads on 2016-01-15
I have tried following [a more detailed guide from xpressrazor]("https://xpressrazor.wordpress.com/2013/05/09/creating-ubuntu-packages/"), but it fails when running *debuild*, with the following cryptic messages:

```
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
debuild: fatal error at line 1364:
dpkg-buildpackage -rfakeroot -D -us -uc failed
```

Any hints are welcome. Thank you.

---

