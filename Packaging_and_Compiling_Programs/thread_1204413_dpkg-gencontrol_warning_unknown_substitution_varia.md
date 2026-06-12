---
title: "dpkg-gencontrol: warning: unknown substitution variable"
date: 2009-07-04
forum: Packaging and Compiling Programs
---

### Post by MrLobster on 2009-07-04
I'm trying to make a .deb file out of a python application for the first time and get these warnings:
```

dpkg-gencontrol: warning: unknown substitution variable ${python:Depends}
dpkg-gencontrol: warning: unknown substitution variable ${shlibs:Depends}
dpkg-gencontrol: warning: unknown substitution variable ${misc:Depends}
```

Here are the "Depends" lines of my control file:
```
Build-Depends:  python-support (>= 0.5.3), debhelper (>= 5)

and

Depends: python (>= 2.5), python (<< 3.0), python-opengl, python-wxgtk2.8, ${python:Depends}, ${shlibs:Depends}, ${misc:Depends}
```


I'm also trying to use dh_support to get my python modules to compile on installation and so far it isn't working.  Everything thing else appears to work with the .deb file that gets created.  Any idea where my error lies?

---

### Post by MrLobster on 2009-07-05
Half the problem is solved now.  I made a few changes but what I think fixed the .pyc files not being made and the ${python: Depends} warning appearing was by moving dh_pysupport above dh_installdeb in the rules file.  Before I had simply added dh_pysupport to the bottom of the list.

---

### Post by laney on 2009-07-11
Please post your rules file and build log output

---

### Post by MrLobster on 2009-07-11
rules file:
```

#!/usr/bin/make -f
# -*- makefile -*-
# Sample debian/rules that uses debhelper.
# This file was originally written by Joey Hess and Craig Small.
# As a special exception, when this file is copied by dh-make into a
# dh-make output file, you may use that output file without restriction.
# This special exception was added by Craig Small in version 0.37 of dh-make.

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1

PACKAGE=emol

configure: configure-stamp
configure-stamp:
	dh_testdir
	# Add here commands to configure the package.

	touch configure-stamp


build: build-stamp

build-stamp: configure-stamp 
	dh_testdir
	touch build-stamp

clean:
	dh_testdir
	dh_testroot
	rm -f build-stamp configure-stamp
	dh_clean 

install: build
	dh_testdir
	dh_testroot
	dh_clean -k
	dh_installdirs

	### insert your commands here
	mkdir -p $(CURDIR)/debian/$(PACKAGE)/usr/bin
	mkdir -p $(CURDIR)/debian/$(PACKAGE)/usr/share/$(PACKAGE)
	mkdir -p $(CURDIR)/debian/$(PACKAGE)/usr/share/applications	
	mkdir -p $(CURDIR)/debian/$(PACKAGE)/usr/share/pixmaps
	mkdir -p $(CURDIR)/debian/$(PACKAGE)/usr/share/man/man1
	
	cp emol $(CURDIR)/debian/$(PACKAGE)/usr/bin/
	cp *.py $(CURDIR)/debian/$(PACKAGE)/usr/share/$(PACKAGE)/
	cp emol.desktop $(CURDIR)/debian/$(PACKAGE)/usr/share/applications/
	cp emol.svg $(CURDIR)/debian/$(PACKAGE)/usr/share/pixmaps/
	cp emol.1.gz $(CURDIR)/debian/$(PACKAGE)/usr/share/man/man1

# Build architecture-independent files here.
binary-indep: build install
# We have nothing to do by default.

# Build architecture-dependent files here.
binary-arch: build install
	dh_testdir
	dh_testroot
	dh_installchangelogs 
	dh_installdocs
	dh_installexamples
#	dh_install
#	dh_installmenu
#	dh_installdebconf	
#	dh_installlogrotate
#	dh_installemacsen
#	dh_installpam
#	dh_installmime
#	dh_python
	dh_pysupport
#	dh_installinit
#	dh_installcron
#	dh_installinfo
	dh_installman
	dh_link
	dh_strip
	dh_compress
	dh_fixperms
#	dh_perl
#	dh_makeshlibs
	dh_installdeb
	dh_shlibdeps
	dh_gencontrol
	dh_md5sums
	dh_builddeb

	
binary: binary-indep binary-arch
.PHONY: build clean binary-indep binary-arch binary install configure

```


dpkg-buildpackage output:
```

erik@heron:~/Desktop/emol-packaging/emol-1.0.0$ sudo dpkg-buildpackage 
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package emol
dpkg-buildpackage: source version 1.0.0
dpkg-buildpackage: source changed by Erik Thompson <mrlobster99@gmail.com>
dpkg-buildpackage: host architecture i386
 debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
dh_clean 
 dpkg-source -b emol-1.0.0
dpkg-source: building emol in emol_1.0.0.tar.gz
dpkg-source: building emol in emol_1.0.0.dsc
 debian/rules build
dh_testdir
# Add here commands to configure the package.
touch configure-stamp
dh_testdir
touch build-stamp
 debian/rules binary
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
### insert your commands here
mkdir -p /home/erik/Desktop/emol-packaging/emol-1.0.0/debian/emol/usr/bin
mkdir -p /home/erik/Desktop/emol-packaging/emol-1.0.0/debian/emol/usr/share/emol
mkdir -p /home/erik/Desktop/emol-packaging/emol-1.0.0/debian/emol/usr/share/applications	
mkdir -p /home/erik/Desktop/emol-packaging/emol-1.0.0/debian/emol/usr/share/pixmaps
mkdir -p /home/erik/Desktop/emol-packaging/emol-1.0.0/debian/emol/usr/share/man/man1
cp emol /home/erik/Desktop/emol-packaging/emol-1.0.0/debian/emol/usr/bin/
cp *.py /home/erik/Desktop/emol-packaging/emol-1.0.0/debian/emol/usr/share/emol/
cp emol.desktop /home/erik/Desktop/emol-packaging/emol-1.0.0/debian/emol/usr/share/applications/
cp emol.svg /home/erik/Desktop/emol-packaging/emol-1.0.0/debian/emol/usr/share/pixmaps/
cp emol.1.gz /home/erik/Desktop/emol-packaging/emol-1.0.0/debian/emol/usr/share/man/man1
dh_testdir
dh_testroot
dh_installchangelogs 
dh_installdocs
dh_installexamples
dh_pysupport
dh_installman
dh_link
dh_strip
dh_compress
dh_fixperms
dh_installdeb
dh_shlibdeps
dh_gencontrol
dpkg-gencontrol: warning: unknown substitution variable ${shlibs:Depends}
dpkg-gencontrol: warning: unknown substitution variable ${misc:Depends}
dh_md5sums
dh_builddeb
dpkg-deb: building package `emol' in `../emol_1.0.0_all.deb'.
 signfile emol_1.0.0.dsc
gpg: WARNING: unsafe ownership on configuration file `/home/erik/.gnupg/gpg.conf'
gpg: skipped "Erik Thompson <mrlobster99@gmail.com>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available

 dpkg-genchanges  >../emol_1.0.0_i386.changes
dpkg-genchanges: including full source code in upload
dpkg-buildpackage: full upload; Debian-native package (full source is included)
dpkg-buildpackage: warning: Failed to sign .dsc and .changes file
erik@heron:~/Desktop/emol-packaging/emol-1.0.0$

```

---

### Post by laney on 2009-07-16
Alright cool as long as builds fine then there shouldn't be any problems. All that those warnings mean is that no helper has inserted any dependencies in those substitution fields. Nothing to worry about.

---

