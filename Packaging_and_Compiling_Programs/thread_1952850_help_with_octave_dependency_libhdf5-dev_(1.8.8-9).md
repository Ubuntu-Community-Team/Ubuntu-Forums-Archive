---
title: "help with octave dependency libhdf5-dev (1.8.8-9)"
date: 2012-04-05
forum: Packaging and Compiling Programs
---

### Post by hackTHEgibson on 2012-04-05
Hi I am trying to package octave3.6.1 without changes from debian unstable.  The build fails because one of the dependencies is not met.  Specifically libhdf5-dev is version 1.84 and needs to be (>=1.8.8).  So my question is how to get version 1.8.8 into the build. It exists in unstable as well.  But I don't know how to get into the virtual machine building octave on my PPA.  Do I have to put a call to it inside the octave code? Or can I build it separately outside and link to it somehow?

---

### Post by MadCow108 on 2012-04-05
libhdf5-dev is still libhdf5-serial-dev in ubuntu.
Depending on whether octave really needs 1.8.8 or not you can try just replacing the dependency.
Maybe the version requirement is too strict in the debian package (hard to say, no proper documentation of the change in the git log)

replacing ubuntu's hdf5 can be problematic as the new version is not compatible with the old one.

---

### Post by hackTHEgibson on 2012-04-05
So I tried creating a different PPA to build libhdf5 in but it failed too(**amd64 build succeeded but i386 failed**)  Can anyone tell me what went wrong with the i386?

```
touch build-stamp-mpich2
 /usr/bin/fakeroot debian/rules binary
dh_testdir
dh_testroot
dh_install -plibhdf5-doc -X Dependencies -X Makefile.in -X CppUserNotes.doc
cp: cannot stat `debian/tmp/html': No such file or directory
dh_install: cp -a debian/tmp/html debian/libhdf5-doc//usr/share/doc/libhdf5-doc/ returned exit code 1
make: *** [install-doc] Error 2
dpkg-buildpackage: error: /usr/bin/fakeroot debian/rules binary gave error exit status 2
******************************************************************************
Build finished at 20120406-0019
FAILED [dpkg-buildpackage died]
Purging chroot-autobuild/build/buildd/hdf5-1.8.8
```

---

### Post by hackTHEgibson on 2012-04-06
Here is the debian/rules code that I think is referenced in the build code.  I don't know what is wrong.  Also once the hdf5-amd64 built, the octave3.6.1-amd64 was able to build so at least I'm on the right track.  

```
install-mpich2: build-stamp-mpich2
        dh_testdir
        dh_testroot
        -mkdir debian/build-mpich2/tmpinst
        $(MAKE) -C debian/build-mpich2/ install prefix=$(CURDIR)/debian/build-mpich2/tmpinst/usr
        dh_install -p$(mpich2pack) -p$(package)-mpich2-dev \
                --sourcedir=debian/build-mpich2/tmpinst

install-doc: build-indep
        dh_testdir
        dh_testroot
        dh_install -p$(package)-doc -X Dependencies -X Makefile.in -X CppUserNotes.doc

binary-indep: install-doc
        dh_testdir
        dh_testroot
        dh_installdocs -i
        dh_installchangelogs -i -k release_docs/RELEASE.txt
        dh_compress -i -X.pdf
        dh_fixperms -i
        dh_installdeb -i
        dh_lintian -i
        dh_gencontrol -i

```

---

### Post by MadCow108 on 2012-04-06
doesn't simply renaming the dependency of octave work?

hdf5 is a significant transition, it will most likely only be done after 12.04 in ubuntu.

---

