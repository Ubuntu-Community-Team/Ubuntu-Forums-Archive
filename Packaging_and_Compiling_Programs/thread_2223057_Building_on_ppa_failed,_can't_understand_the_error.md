---
title: "Building on ppa failed, can't understand the error."
date: 2014-05-09
forum: Packaging and Compiling Programs
---

### Post by VinsS on 2014-05-09
Hi,

I'm trying to build a package on my ppa.

This package is a Python binding for a lib that I've written and packaged on the same ppa.

This is the control file:
---------------------------------------------------------------------
Source: python-cvengine
Section: python
Priority: optional
Maintainer: Vincent Vande Vyvre <vincent.vandevyvre@swing.be>
Uploaders: Vincent Vande Vyvre <vincent.vandevyvre@swing.be>
Build-Depends: debhelper (>= 7.0.50),
    python-all-dev (>= 2.6.6-3),
    gcc (>= 3.3),
    python-sip (>= 4.12.0),
    python-sip-dev (>= 4.12.0),
    libopencv-dev (>= 2.3),
    libcvaux-dev (>= 2.3),
    libcv-dev (>= 2.3),
    libcv2.3 ,
    libcvaux2.3 ,
    libhighgui2.3 
Standards-Version: 3.9.2
X-Python-Version: >= 2.6
Homepage: [http://bazaar.launchpad.net/~vincent-vandevyvre/oqapy/2.0/](http://bazaar.launchpad.net/~vincent-vandevyvre/oqapy/2.0/)

Package: python-cvengine
Architecture: any
Provides: ${python:Provides}
Depends: ${shlibs:Depends}, ${python:Depends}, ${misc:Depends}, 
    python-sip (>= 4.12.0), 
    libcv2.3, 
    libcvaux2.3, 
    libhighgui2.3
Description: Python binding for libcvengine
 libcvengine is a C++ library for image processing.
 .
 This package provide the Python 2.x binding for lib cvengine.
---------------------------------------------------------------------

The rules file:
---------------------------------------------------------------------
#!/usr/bin/make -f

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1

PYVERSIONS=$(shell pyversions -vr debian/control)

override_dh_auto_configure:
override_dh_auto_build:
    set -e; \
    /bin/sh build.sh; \
    for v in $(PYVERSIONS) ; do \
        PYTHON=python$$v ; \
        $$PYTHON configure; \
        make ; \
        make install ; \
    done

override_dh_auto_clean:
override_dh_auto_install:
override_dh_installchangelogs:
    dh_installchangelogs NEWS

build: 
build-arch:
build-indep:
build-stamp:
clean:
install: build
    dh --with python2 install

# Build architecture-independent files here.
binary-indep:
# Build architecture-dependent files here.
binary-arch:

binary:
.PHONY: build clean binary-indep binary-arch binary install

---------------------------------------------------------------------

The python-cvengine_0.1.1.orig.tar.gz contains:

python-cvengine-0.1.1
    - cvengine.h
    - cvengine.cpp
    - cvengine.sip
    - configure.py
    - cvengine.sbf
    - NEWS

And that's the error when building:
---------------------------------------------------------------------
[skip the begining]
...
RUN: /usr/share/launchpad-buildd/slavebin/sbuild-package ['sbuild-package', 'PACKAGEBUILD-5988856', 'amd64', 'precise', '--nolog', '--batch', '--archive=ubuntu', '--dist=precise', '--purpose=PPA', '--architecture=amd64', '--comp=main', 'python-cvengine_0.1.1-0ubuntu1.dsc']
Initiating build PACKAGEBUILD-5988856 with 2 jobs across 2 processor cores.
Kernel reported to sbuild: 2.6.24-32-xen #1 SMP Mon Dec 3 16:12:25 UTC 2012 x86_64
Automatic build of python-cvengine_0.1.1-0ubuntu1 on gold by sbuild/amd64 1.170.5
Build started at 20140508-1606
******************************************************************************
python-cvengine_0.1.1-0ubuntu1.dsc exists in cwd
** Using build dependencies supplied by package:
Build-Depends: debhelper (>= 7.0.50), python-all-dev (>= 2.6.6-3), gcc (>= 3.3), python-sip (>= 4.12.0), python-sip-dev (>= 4.12.0), libopencv-dev (>= 2.3), libcvaux-dev (>= 2.3), libcv-dev (>= 2.3), libcv2.3, libcvaux2.3, libhighgui2.3
Checking for already installed source dependencies...
debhelper: missing
python-all-dev: missing
gcc: already installed (4:4.6.3-1ubuntu5 >= 3.3 is satisfied)
python-sip: missing
python-sip-dev: missing
libopencv-dev: missing
libcvaux-dev: missing
libcv-dev: missing
libcv2.3: missing
libcvaux2.3: missing
libhighgui2.3: missing
Checking for source dependency conflicts...
  /usr/bin/sudo /usr/bin/apt-get --purge $CHROOT_OPTIONS -q -y install debhelper python-all-dev python-sip python-sip-dev libopencv-dev libcvaux-dev libcv-dev libcv2.3 libcvaux2.3 libhighgui2.3
Reading package lists...
Building dependency tree...
Reading state information...
The following extra packages will be installed:
...
[skip the install]
dpkg-source: warning: -sn is not a valid option for Dpkg::Source::Package::V3::quilt
gpgv: Signature made Thu May  8 07:04:58 2014 UTC using RSA key ID B93DA448
gpgv: Can't check signature: public key not found
dpkg-source: warning: failed to verify signature on ./python-cvengine_0.1.1-0ubuntu1.dsc
dpkg-source: info: extracting python-cvengine in python-cvengine-0.1.1
dpkg-source: info: unpacking python-cvengine_0.1.1.orig.tar.gz
dpkg-source: info: unpacking python-cvengine_0.1.1-0ubuntu1.debian.tar.gz
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): -D_FORTIFY_SOURCE=2
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions -Wl,-z,relro
dpkg-buildpackage: source package python-cvengine
dpkg-buildpackage: source version 0.1.1-0ubuntu1
 dpkg-source --before-build python-cvengine-0.1.1
dpkg-buildpackage: host architecture amd64
 /usr/bin/fakeroot debian/rules clean
make: Nothing to be done for `clean'.
 debian/rules build
make: Nothing to be done for `build'.
 /usr/bin/fakeroot debian/rules binary-arch
make: Nothing to be done for `binary-arch'.
 dpkg-genchanges -B -mUbuntu/lpia Build Daemon <buildd@gold.ppa> >../python-cvengine_0.1.1-0ubuntu1_amd64.changes
dpkg-genchanges: arch-specific upload - not including arch-independent packages
dpkg-genchanges: error: cannot read files list file: No such file or directory
dpkg-buildpackage: error: dpkg-genchanges gave error exit status 2
******************************************************************************
Build finished at 20140508-1608
FAILED [dpkg-buildpackage died]
******************************************************************************
Finished at 20140508-1608
Build needed 00:00:01, 204k disk space
RUN: /usr/share/launchpad-buildd/slavebin/scan-for-processes ['scan-for-processes', 'PACKAGEBUILD-5988856']
Scanning for processes to kill in build /home/buildd/build-PACKAGEBUILD-5988856/chroot-autobuild...
RUN: /usr/share/launchpad-buildd/slavebin/umount-chroot ['umount-chroot', 'PACKAGEBUILD-5988856']
Unmounting chroot for build PACKAGEBUILD-5988856...
RUN: /usr/share/launchpad-buildd/slavebin/remove-build ['remove-build', 'PACKAGEBUILD-5988856']
Removing build PACKAGEBUILD-5988856
---------------------------------------------------------------------

The error is the same for the i386

Am I missing something in my package ?


Thank's for all advices.

---

### Post by VinsS on 2014-05-11
After several try, I've simplified the rules file

----------------------------------------------------------------------------------------------------
#!/usr/bin/make -f

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1

%:
    dh $@ --with python2

PYVERSIONS=$(shell pyversions -vr debian/control)

override_dh_auto_build:
    set -e ; \
    for v in $(PYVERSIONS) ; do \
        PYTHON=python$$v ; \
        $$PYTHON configure ; \
        make ; \
        cp cvengine.so debian/tmp ; \
    done

override_dh_installchangelogs:
    dh_installchangelogs NEWS

override_dh_gencontrol:
    dh_gencontrol

build: build-arch ;

binary-arch:
    dh build --with=python2

install: build
    dh --with python2 install
--------------------------------------------------------------------------------------

Now, thats works.

---

