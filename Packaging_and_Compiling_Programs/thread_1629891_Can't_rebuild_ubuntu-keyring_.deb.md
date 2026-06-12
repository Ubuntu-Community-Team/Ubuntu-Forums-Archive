---
title: "Can't rebuild ubuntu-keyring .deb"
date: 2010-11-24
forum: Packaging and Compiling Programs
---

### Post by dviljoen on 2010-11-24
I've been trying to build a custom install CD for a preconfigured server and have been following the steps outlined in [https://help.ubuntu.com/community/InstallCDCustomization]("http://https://help.ubuntu.com/community/InstallCDCustomization")

However, when I get to the step for rebuilding the keyring debian package to add my Extras component, it fails with:
> dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package ubuntu-keyring
dpkg-buildpackage: source version 2010.+09.30
dpkg-buildpackage: host architecture i386
 dpkg-source --before-build ubuntu-keyring-2010.+09.30
 fakeroot debian/rules clean
test -f keyrings/ubuntu-archive-keyring.gpg
rm -f foo foo.asc *.bak *~ */*~ debian/files* debian/*substvars
rm -rf debian/tmp debian/ubuntu-keyring-udeb
 dpkg-source -b ubuntu-keyring-2010.+09.30
dpkg-source: warning: no source format specified in debian/source/format, see dpkg-source(1)
dpkg-source: info: using source format `1.0'
dpkg-source: info: building ubuntu-keyring in ubuntu-keyring_2010.+09.30.tar.gz
dpkg-source: error: unable to rename `/home/dviljoen/share/keys/ubuntu-keyring_2010.+09.30.tar.gz.new.2Cq8sD' (newly created) to `ubuntu-keyring_2010.+09.30.tar.gz': Text file busy
dpkg-buildpackage: error: dpkg-source -b ubuntu-keyring-2010.+09.30 gave error exit status 26
dviljoen@ubuntu:~/share/keys/ubuntu-keyring-2010.+09.30$ I've tried several different versions of Ubuntu (from 9.04 through 10.10) and they all exhibit the same error.  Can someone tell me why?

---

