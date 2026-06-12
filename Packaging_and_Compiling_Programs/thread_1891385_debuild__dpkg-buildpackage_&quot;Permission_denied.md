---
title: "debuild / dpkg-buildpackage: &quot;Permission denied&quot;"
date: 2011-12-05
forum: Packaging and Compiling Programs
---

### Post by djsephiroth on 2011-12-05
Debianizing "plain" source.   

Source is in /usr/src/foo-1.2.3/, where "foo-1.2.3" == "nslink_4.28.1".

When I run debuild or dpkg-buildpackage, I get "permission denied" errors. I have read that running build tools with sudo is a Bad Thing, so I am uncertain of what to do.

pbuilder seems like an obvious answer, but I'm without a .dsc file to feed it. When I try to make one with debuild -S, I get... more permissions errors.

```
$ debuild -S
tee: ../nslink_4.28.1-1_source.build: Permission denied
 dpkg-buildpackage -rfakeroot -d -us -uc -S
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package nslink
dpkg-buildpackage: source version 4.28.1-1
dpkg-buildpackage: source changed by Shelby Skalnik <sskalnik@gmail.com>
 dpkg-source --before-build nslink-4.28.1
 fakeroot debian/rules clean
dh clean 
   dh_testdir
   dh_auto_clean
make[1]: Entering directory `/usr/src/nslink-4.28.1'
rm -f *.o 
rm -f *.ko
rm -f .nslink*
rm -f nslinkd 
rm -f *~ 
rm -f lput 
rm -f vtst 
rm -f .kver 
rm -f nslinkadmin 
rm -f nslinkrelease
rm -rf nslink
rm -rf nslink.mod.c
rm -rf .tmp*
rm -rf *.symvers
rm -rf Module.markers
rm -rf modules.order
make[1]: Leaving directory `/usr/src/nslink-4.28.1'
   dh_clean
 dpkg-source -b nslink-4.28.1
dpkg-source: info: using source format `3.0 (quilt)'
Error in tempdir() using nslink-4.28.1.orig.XXXXXX: Could not create directory nslink-4.28.1.orig.N2hWoz: Permission denied at /usr/share/perl5/Dpkg/Source/Package/V2.pm line 334
dpkg-source: info: building nslink using existing ./nslink_4.28.1.orig.tar.gz
dpkg-buildpackage: error: dpkg-source -b nslink-4.28.1 gave error exit status 13
debuild: fatal error at line 1348:
dpkg-buildpackage -rfakeroot -d -us -uc -S failed

```

---

### Post by djsephiroth on 2011-12-05
Moved the source folder to ~, which fixed the "permission denied" errors. 

However, I am now getting pbuilder errors:

```
make[1]: Leaving directory `/tmp/buildd/nslink-4.28.1'
   dh_clean
 dpkg-source -b nslink-4.28.1
dpkg-source: info: using source format `3.0 (quilt)'
dpkg-source: info: building nslink using existing ./nslink_4.28.1.orig.tar.gz
dpkg-source: info: building nslink in nslink_4.28.1-1.debian.tar.gz
dpkg-source: info: building nslink in nslink_4.28.1-1.dsc
 debian/rules build
dh build 
   dh_testdir
   dh_auto_configure
   dh_auto_build
make[1]: Entering directory `/tmp/buildd/nslink-4.28.1'
make -C  SUBDIRS=/tmp/buildd/nslink-4.28.1 modules
make: Entering an unknown directory
make: *** SUBDIRS=/tmp/buildd/nslink-4.28.1: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [all] Error 2
make[1]: Leaving directory `/tmp/buildd/nslink-4.28.1'
dh_auto_build: make -j1 returned exit code 2
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
E: Failed autobuilding of package
I: unmounting /var/cache/pbuilder/ccache filesystem
I: unmounting /tmp filesystem
I: unmounting /home/sskalnik/pbuilder filesystem
I: unmounting dev/pts filesystem
I: unmounting proc filesystem
I: cleaning the build env 
I: removing directory /var/cache/pbuilder/build//16433 and its subdirectories
```

Same thing for debuild:

```
$ debuild -us -uc -b
 dpkg-buildpackage -rfakeroot -D -us -uc -b
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package nslink
dpkg-buildpackage: source version 4.28.1-1
 dpkg-source --before-build nslink-4.28.1
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
dh clean 
   dh_testdir
   dh_auto_clean
make[1]: Entering directory `/home/sskalnik/hnnnngh/nslink-4.28.1'
rm -f *.o 
rm -f *.ko
rm -f .nslink*
rm -f nslinkd 
rm -f *~ 
rm -f lput 
rm -f vtst 
rm -f .kver 
rm -f nslinkadmin 
rm -f nslinkrelease
rm -rf nslink
rm -rf nslink.mod.c
rm -rf .tmp*
rm -rf *.symvers
rm -rf Module.markers
rm -rf modules.order
make[1]: Leaving directory `/home/sskalnik/hnnnngh/nslink-4.28.1'
   dh_clean
 debian/rules build
dh build 
   dh_testdir
   dh_auto_configure
   dh_auto_build
make[1]: Entering directory `/home/sskalnik/hnnnngh/nslink-4.28.1'
make -C  SUBDIRS=/home/sskalnik/hnnnngh/nslink-4.28.1 modules
make: Entering an unknown directory
make: *** SUBDIRS=/home/sskalnik/hnnnngh/nslink-4.28.1: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/sskalnik/hnnnngh/nslink-4.28.1'
dh_auto_build: make -j1 returned exit code 2
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
debuild: fatal error at line 1348:
dpkg-buildpackage -rfakeroot -D -us -uc -b failed

```

---

### Post by djsephiroth on 2011-12-06
Fixed!

Note the blank argument to -C. 

The Makefile was set up to find the linux headers in the same directory. It didn't find them, so it passed nothing to -C.

---

### Post by djsephiroth on 2011-12-09
See also [http://ubuntuforums.org/showthread.php?t=1891802](http://ubuntuforums.org/showthread.php?t=1891802) for info on how this can be resolved.

---

