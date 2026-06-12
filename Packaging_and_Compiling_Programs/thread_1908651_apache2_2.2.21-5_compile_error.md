---
title: "apache2 2.2.21-5 compile error"
date: 2012-01-13
forum: Packaging and Compiling Programs
---

### Post by ptn107 on 2012-01-13
Took apache 2.2.21-5 from Debian wheezy and trying to compile on Ubuntu 11.10 x64.  All dependencies are satisfied.  Build fails both locally and on launchpad for both architectures.  This is the error:
```
cp: cannot stat `debian/tmp/usr/share/apache2/icons': No such file or directory
dh_install: cp -a debian/tmp/usr/share/apache2/icons debian/apache2.2-common//usr/share/apache2/ returned exit code 1
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: fakeroot debian/rules binary-arch gave error exit status 2
debuild: fatal error at line 1348:
dpkg-buildpackage -rfakeroot -D -us -uc -B failed
```

---

