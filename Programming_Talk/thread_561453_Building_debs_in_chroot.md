---
title: "Building debs in chroot"
date: 2007-09-27
forum: Programming Talk
---

### Post by Kow on 2007-09-27
I have a i486 chroot setup with dchroot and dpkg-buildpackage is causing all kinds of issues, particularly with the firefox source deb. dpkg-architecture returns the correct arch and system (i486) but when I build the package the process fails after it tries using xptcinvoke_x86_64_linux.cpp:

 dpkg-architecture
DEB_BUILD_ARCH=i386
DEB_BUILD_ARCH_OS=linux
DEB_BUILD_ARCH_CPU=i386
DEB_BUILD_GNU_CPU=i486
DEB_BUILD_GNU_SYSTEM=linux-gnu
DEB_BUILD_GNU_TYPE=i486-linux-gnu
DEB_HOST_ARCH=i386
DEB_HOST_ARCH_OS=linux
DEB_HOST_ARCH_CPU=i386
DEB_HOST_GNU_CPU=i486
DEB_HOST_GNU_SYSTEM=linux-gnu
DEB_HOST_GNU_TYPE=i486-linux-gnu

dpkg-buildpackage -rfakeroot -b starts with:
dpkg-buildpackage: source package is firefox
dpkg-buildpackage: source version is 2.0.0.7-0ubuntu0
dpkg-buildpackage: source changed byv***** <*****@localhost>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 2.0.0.7-0ubuntu0

but fails at this point:
make[8]: Entering directory `/home/****/sources/firefox-2.0.0.7/build-tree/mozilla/xpcom/reflect/xptcall/src/md/unix'
xptcinvoke_x86_64_linux.cpp

So there is an obvious issue somewhere...

---

