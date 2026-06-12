---
title: "beginner needs help with openssh-lpk patch"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by xtech on 2012-06-26
So i'm trying to patch openssh on ubuntu 12.04LTS, to work with ssh keys/cert and ldap authentication.
here is what i have dode so far..
- downloaded  contrib-openssh-lpk-5.1p1-0.3.10.patch
- downloaded openssh5.1 from lenny source
- patched patch -Np1 -i contrib-openssh-lpk-5.1p1-0.3.10.patch
- added confflags += --with-ldap flag
and then tried to build with debuild -uc -us, but got some errors..

```
parsechangelog/debian: warning:     debian/changelog(l17): badly formatted heading line
LINE: * patched openssh-lpk
 dpkg-buildpackage -rfakeroot -D -us -uc
dpkg-buildpackage: warning: using a gain-root-command while being root
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): -D_FORTIFY_SOURCE=2
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions -Wl,-z,relro
parsechangelog/debian: warning:     debian/changelog(l17): badly formatted heading line
LINE: * patched openssh-lpk
dpkg-buildpackage: source package openssh
dpkg-buildpackage: source version 1:5.1p1-5
dpkg-buildpackage: source changed by root <root@srv6-lab.pkamk.fi>
 dpkg-source --before-build openssh-5.1p1
dpkg-buildpackage: host architecture amd64
parsechangelog/debian: warning: openssh-5.1p1/debian/changelog(l17): badly formatted heading line
LINE: * patched openssh-lpk
dpkg-checkbuilddeps: Unmet build dependencies: libwrap0-dev | libwrap-dev zlib1g-dev (>= 1:1.2.3-1) libssl-dev (>= 0.9.8-1) libpam0g-dev | libpam-dev libgtk2.0-dev libedit-dev debhelper (>= 5.0.22) libselinux1-dev libkrb5-dev | heimdal-dev
dpkg-buildpackage: warning: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: warning: (Use -d flag to override.)
debuild: fatal error at line 1350:
dpkg-buildpackage -rfakeroot -D -us -uc failed
```

help me please :-)
sorry for my english

---

