---
title: "Attempting to package monsoon"
date: 2008-08-06
forum: Packaging and Compiling Programs
---

### Post by mick8985 on 2008-08-06
Hi, I haven't done much in the way of packaging before and I want to dip my foot in the water so I had a go at packaging monsoon, but I have hit a brick wall and the guides don't do much in the way of helping you when things don't work.
```
michael@michael-desktop:~/Packaging/monsoon/monsoon-0.15/debian$ debuild -S -sa
 dpkg-buildpackage -rfakeroot -d -us -uc -S -sa
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package monsoon
dpkg-buildpackage: source version 0.15-1ubuntu1
dpkg-buildpackage: source changed by Michael Stephenson <mickstephenson@gmail.com>
 fakeroot debian/rules clean
/usr/bin/fakeroot: 166: debian/rules: Permission denied
dpkg-buildpackage: failure: fakeroot debian/rules clean gave error exit status 126
debuild: fatal error at line 1329:
dpkg-buildpackage -rfakeroot -d -us -uc -S -sa failed

```
I have tried making rules executable using chmod +x but that obviously isn't the problem, could someone point me in the right direction?

---

