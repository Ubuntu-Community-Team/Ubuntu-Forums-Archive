---
title: "Building a kernel module package"
date: 2011-04-03
forum: Packaging and Compiling Programs
---

### Post by KNRO on 2011-04-03
I'm having a problem building a package for Finger Lakes Instruments (FLI) USB module. There are no issues in compiling and installing the module by running make, make install...etc. Here is the makefile:

```

obj-m        := fliusb.o

KDIR        ?= /lib/modules/$(shell uname -r)/build
KROOT           ?= /lib/modules/$(shell uname -r)
PWD        := $(shell pwd)

EXTRA_CFLAGS        += -O2 -Wall

#EXTRA_CFLAGS        += -DDEBUG    # enable debug messages
#EXTRA_CFLAGS        += -DASYNCWRITE    # enable asynchronous writes
EXTRA_CFLAGS        += -DSGREAD    # enable scatter-gather reads

all: module cleanup

module:
    $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

cleanup:
    rm -f *.o .*.cmd *.mod.c; rm -rf .tmp_versions

install:
    cp *.h /usr/include
    cp fliusb.ko $(KROOT)/kernel/drivers/usb
    insmod fliusb.ko
       
clean: cleanup
    rm -f *.ko test

```In the debian/rules file I have:

```

#!/usr/bin/make -f

include /usr/share/cdbs/1/class/makefile.mk
include /usr/share/cdbs/1/rules/debhelper.mk

```And finally, in debian/control, I have:

```

Source: fliusb
Section: libs
Priority: extra
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Build-Depends: debhelper (>= 6), cdbs
Standards-Version: 3.8.0

Package: fliusb
Architecture: any
Depends: ${shlibs:Depends}, ${misc:Depends}
Description: FLI USB Kernel Driver
 .
 This driver is required to operate FLI USB CCD & Filter Wheel under Linux.

```However, when I run pbuilder, I end up with the following error:

```

I: Building the package
I: Running cd tmp/buildd/*/ && dpkg-buildpackage -us -uc  -rfakeroot
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package fliusb
dpkg-buildpackage: source version 1.0-0ubuntu1
dpkg-buildpackage: source changed by Jasem Mutlaq <mutlaqja@ikarustech.com>
dpkg-buildpackage: host architecture i386
 dpkg-source --before-build fliusb-1.0
 fakeroot debian/rules clean
test -x debian/rules
dh_testroot
rm -f debian/stamp-makefile-build debian/stamp-makefile-install
/usr/bin/make  -C . CFLAGS="-g -O2 -g -Wall -O2" CXXFLAGS="-g -O2 -g -Wall -O2" CPPFLAGS="" LDFLAGS="-Wl,-Bsymbolic-functions"  -k clean
make[1]: Entering directory `/tmp/buildd/fliusb-1.0'
rm -f *.o .*.cmd *.mod.c; rm -rf .tmp_versions
rm -f *.ko test
make[1]: Leaving directory `/tmp/buildd/fliusb-1.0'
dh_clean 
 dpkg-source -b fliusb-1.0
dpkg-source: warning: no source format specified in debian/source/format, see dpkg-source(1)
dpkg-source: info: using source format `1.0'
dpkg-source: info: building fliusb using existing fliusb_1.0.orig.tar.gz
dpkg-source: info: building fliusb in fliusb_1.0-0ubuntu1.diff.gz
dpkg-source: info: building fliusb in fliusb_1.0-0ubuntu1.dsc
 debian/rules build
test -x debian/rules
mkdir -p "."
/usr/bin/make  -C . CFLAGS="-g -O2 -g -Wall -O2" CXXFLAGS="-g -O2 -g -Wall -O2" CPPFLAGS="" LDFLAGS="-Wl,-Bsymbolic-functions"  
make[1]: Entering directory `/tmp/buildd/fliusb-1.0'
/usr/bin/make -C /lib/modules/2.6.35-28-generic-pae/build SUBDIRS=/tmp/buildd/fliusb-1.0 modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.35-28-generic-pae/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [module] Error 2
make[1]: Leaving directory `/tmp/buildd/fliusb-1.0'
make: *** [debian/stamp-makefile-build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
E: Failed autobuilding of package
I: unmounting dev/pts filesystem
I: unmounting proc filesystem
I: cleaning the build env 
I: removing directory /var/cache/pbuilder/build//21257 and its subdirectories

```So  **/lib/modules/2.6.35-28-generic-pae/build **doesn't exist, and I'm not sure how to make pbuilder install the appropriate kernel headers. I also took a look at other kernel module examples and there doesn't seem to be one consistent way of resolving this.

Any help is appreciated!

---

### Post by danwood76 on 2011-04-05
In your makefile it is instructing make to change to KDIR before compiling.
As this directory doesn't exist its failing.

Try either running make with sudo and/or creating the /lib/modules/2.6.35-28-generic-pae/build directory as well.

Its possible that the -C is actually not needed and the makefile could be fixed to remove it but makefile syntax is quite complex and I would leave it alone if you don't know how.

---

