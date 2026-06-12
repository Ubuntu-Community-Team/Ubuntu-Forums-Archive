---
title: "kernel debuild help"
date: 2010-11-19
forum: Packaging and Compiling Programs
---

### Post by alongenemylines on 2010-11-19
I've had no problems compiling kernels (.debs) with make-kpkg, but I'd like to use debuild (or anything for that matter) so I can upload my kernels to a PPA.

I've downloaded the 2.6.36 source from kernel.org, extracted it, patched it, used dh_make (in the linux-2.6.36 dir)to create the debian directory files, then ran debuild.


scott@windy:~/Downloads/linux-2.6.36$ debuild
 dpkg-buildpackage -rfakeroot -D -us -uc
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package linux
dpkg-buildpackage: source version 2.6.36-1
dpkg-buildpackage: source changed by Scott Franke <scott@unknown>
 dpkg-source --before-build linux-2.6.36
dpkg-buildpackage: host architecture amd64
 fakeroot debian/rules clean
dh clean 
   dh_testdir
   dh_auto_clean
make[1]: Entering directory `/home/scott/Downloads/linux-2.6.36'
  CLEAN   /home/scott/Downloads/linux-2.6.36/debian/
make[1]: Leaving directory `/home/scott/Downloads/linux-2.6.36'
dh_auto_clean: failed to write to debian/linux.debhelper.log: No such file or directory
END failed--call queue aborted.
make: *** [clean] Error 2
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2
debuild: fatal error at line 1337:
dpkg-buildpackage -rfakeroot -D -us -uc failed

---

