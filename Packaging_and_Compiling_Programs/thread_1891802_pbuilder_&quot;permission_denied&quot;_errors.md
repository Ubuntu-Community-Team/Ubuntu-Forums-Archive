---
title: "pbuilder &quot;permission denied&quot; errors"
date: 2011-12-06
forum: Packaging and Compiling Programs
---

### Post by djsephiroth on 2011-12-06
pbuilder asks for my sudo password, but fails with "permission denied" errors.

Example:

```
make[1]: Leaving directory `/tmp/buildd/nslink-4.28.1'
   dh_auto_test
 fakeroot debian/rules binary
dh binary 
   dh_testroot
   dh_prep
   dh_installdirs
   dh_auto_install
make[1]: Entering directory `/tmp/buildd/nslink-4.28.1'
--- Making sure the 'misc' module directory exists...
test -d /lib/modules/3.2.0-3-generic-pae/misc || mkdir /lib/modules/3.2.0-3-generic-pae/misc
--- Copying module to proper directory...
cp *.ko /lib/modules/3.2.0-3-generic-pae/misc
--- Copying the .conf configuration file to /etc...
test ! -f /etc/rpshsi.conf || mv /etc/rpshsi.conf /etc/nslink.conf
test -f /etc/nslink.conf || cp nslink.conf /etc
cp: cannot create regular file `/etc/nslink.conf': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/tmp/buildd/nslink-4.28.1'
dh_auto_install: make -j1 install DESTDIR=/tmp/buildd/nslink-4.28.1/debian/tmp returned exit code 2
make: *** [binary] Error 29
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2
E: Failed autobuilding of package
```

---

### Post by MG&amp;TL on 2011-12-06
Is your makefile installing to / or to $DESTDIR?

Your makefile should look like this (please correct me!):

```

cp <stuff> $(DESTDIR)/etc/
cp <stuff> $(DESTDIR)/moreplaces
```

That way, if you're make-ing normally, it works normally, if you're running a deb package, it installs to where dh says, or where you say. :)

IDK if this helps, but that's what it looks like to me.

---

### Post by djsephiroth on 2011-12-06
That makes sense.

Do I need to prepend $(DESTDIR) to every instance of / in the Makefile?

---

### Post by Bachstelze on 2011-12-06
What does your Makefile look like?

---

### Post by djsephiroth on 2011-12-06
# I am forcing the kernel version so that I build the modules for 3.2 and not 3.0
# I am using Oneiric + pbuilder to build this package for Precise
KVER=3.2.0-3-generic-pae

RM=rm -f
PWD:= $(shell pwd)
CURRENTDATE=$(shell date +%Y%m%d%H%M%S)

#  Find the kernel source.
ifeq ($(shell test -d /usr/src/linux && echo true),true)
  LINUX_SRC=/usr/src/linux
endif
ifeq ($(shell test -d /usr/src/kernel-headers-$(KVER) && echo true),true)
  LINUX_SRC=/usr/src/kernel-headers-$(KVER)
endif
ifeq ($(shell test -d /lib/modules/$(KVER)/build && echo true),true) 
  LINUX_SRC=/lib/modules/$(KVER)/build
endif

LINUX_VERSION=$(shell uname -r | awk '{ split($$0,a,"[.-]"); print a[1]"."a[2]}')

OLD_BUILD=no

ifeq ($(MAKELEVEL),0)
$(warning LINUX_VERSION: $(LINUX_VERSION))
$(warning LINUX_SRC: $(LINUX_SRC))
endif

obj-m += nslink.o
EXTRA_FLAGS += -D__SMP__ -O2 -g

# build targetsfor 2.6, 3.0 kernels
all:
	$(MAKE) -C $(LINUX_SRC) SUBDIRS=$(PWD) modules
	make CFLAGS=-Wall nslinkd
	make CFLAGS=-Wall nslinkadmin
	make CFLAGS=-Wall nslinkrelease

# This used to start out as "nslink.o: nslink.o"...
# Just noting it in case it was actually sane.
nslink.o: nslink.c nslink_int.h nslink.h version.h

nslinkd.o: nslinkd.c nslink.h version.h connectsecure.h

connectsecure.o: connectsecure.c connectsecure.h

nslinkd: nslinkd.o parse.o connectsecure.o
	gcc -Wall -o nslinkd nslinkd.o parse.o connectsecure.o

nslinkadmin: nslinkadmin.c
	gcc -Wall -o nslinkadmin nslinkadmin.c

nslinkrelease: nslinkrelease.c
	$(CC) -Wall -o nslinkrelease nslinkrelease.c

modules: nslink.o mod_nslink.o

# This used to start out as "clean::" - note the double colons.
# Just noting this change in case the original was actually sane.
clean::
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

update-nslinkd:
	@test ! -f /var/run/nslinkd.pid || (echo -e "\n\n\n *** PLEASE STOP THE CURRENT NSLINK DRIVER BEFORE INSTALLING *** \n Commonly '/etc/init.d/nslink stop' to stop the currently runing driver'\n\n\n" && exit 1)
	@echo "--- Updating nslinkd..."
	cp nslinkd /sbin/nslinkd
	strip /sbin/nslinkd
	chmod 755 /sbin/nslinkd
	@echo "--- Issue '/etc/init.d/nslink start' to start the module without rebooting"
	@echo "--- nslinkd update complete"

update-driver:
	@test ! -f /var/run/nslinkd.pid || (echo -e "\n\n\n *** PLEASE STOP THE CURRENT NSLINK DRIVER BEFORE INSTALLING *** \n Commonly '/etc/init.d/nslink stop' to stop the currently runing driver'\n\n\n" && exit 1)
	@echo "--- Making sure the 'misc' module directory exists..."
	test -d /lib/modules/$(KVER)/misc || mkdir /lib/modules/$(KVER)/misc
	@echo "--- Copying module to proper directory..."
	cp *.ko /lib/modules/$(KVER)/misc
	@echo "--- Rebuilding module dependencies..."
	@/sbin/depmod -a -q
	@echo "--- Issue '/etc/init.d/nslink start' to start the module without rebooting"
	@echo "--- nslink driver module update complete"

install:
	@test ! -f /var/run/nslinkd.pid || (echo -e "\n\n\n *** PLEASE STOP THE CURRENT NSLINK DRIVER BEFORE INSTALLING *** \n Commonly '/etc/init.d/nslink stop' to stop the currently runing driver'\n\n\n" && exit 1)
	@echo "--- Making sure the 'misc' module directory exists..."
	test -d /lib/modules/$(KVER)/misc || mkdir /lib/modules/$(KVER)/misc
	@echo "--- Copying module to proper directory..."
	cp *.ko /lib/modules/$(KVER)/misc
	@echo "--- Copying the .conf configuration file to /etc..."
	test ! -f /etc/rpshsi.conf || mv /etc/rpshsi.conf /etc/nslink.conf
	test -f /etc/nslink.conf || cp nslink.conf /etc
	@echo "--- Setting up the 'nslink' startup script..."
	rm -f /etc/init.d/rpshsi
	INITD=/etc/init.d \
	cp rc.nslink /etc/init.d/nslink; \
	chmod 755 $${INITD}/nslink; \
	find /etc/ -type d -name "rc2.d" -exec ln -sf $${INITD}/nslink {}/S83nslink \;; \
	find /etc/ -type d -name "rc3.d" -exec ln -sf $${INITD}/nslink {}/S83nslink \;; \
	find /etc/ -type d -name "rc4.d" -exec ln -sf $${INITD}/nslink {}/S83nslink \;; \
	find /etc/ -type d -name "rc5.d" -exec ln -sf $${INITD}/nslink {}/S83nslink \;; \
	find /etc/ -type d -name "rc0.d" -exec ln -sf $${INITD}/nslink {}/K20nslink \;; \
	find /etc/ -type d -name "rc1.d" -exec ln -sf $${INITD}/nslink {}/K20nslink \;; \
	find /etc/ -type d -name "rc6.d" -exec ln -sf $${INITD}/nslink {}/K20nslink \;
	@echo "--- Copying firmware to /etc..."
	find . -type f -name "rpshsi.bin" -exec cp -p rpshsi.bin /etc/rpshsi.bin \;; \
	find . -type f -name "rpshsi2p.bin" -exec cp -p rpshsi2p.bin /etc/rpshsi2p.bin \;; \
	find . -type f -name "devmast.bin" -exec cp -p devmast.bin /etc/devmast.bin \;
	@echo "--- Installing nslinkd..."
	cp nslinkd /sbin/nslinkd
	strip /sbin/nslinkd
	chmod 755 /sbin/nslinkd
	@echo "--- Installing nslink tools..."
	install --mode=700 nslinkadmin      /usr/sbin
	install --mode=700 nslinktool       /usr/sbin
	install --mode=700 nslinkrelease    /usr/sbin
	install --mode=700 nslinkrelease.py /usr/sbin
	@echo "--- Installing man pages..."
	mkdir -p /usr/local/man/man8
	install --mode=644 *8 /usr/local/man/man8/
	mkdir -p /usr/local/man/man5
	install --mode=644 *5 /usr/local/man/man5/
	@echo "--- Rebuilding module dependencies..."
	@/sbin/depmod -a -q
	@echo "--- Issue '/etc/init.d/nslink start' to start the module without rebooting"
	@echo "--- nslink module installation complete"


uninstall:
	find /lib/modules/$(KVER) -name nslink.ko -exec rm {} \;
	INITD=`find /etc/ -name "init.d"`; \
	find $${INITD}/ -name nslink -exec rm {} \;
	find /etc/ -type l -name "*nslink" -exec rm {} \;
	find /usr/bin/ -name "nslink*" -exec rm {} \;
	find /etc/ -name "rpshsi*.bin" -exec rm {} \;
	find /etc/ -name "devmast*.bin" -exec rm {} \;
	find /usr/local/man/ -name "nslink*" -exec rm {} \;

dist: clean
	tar zcvhf ../devicemaster-linux-$(CURRENTDATE).tar.gz -C .. nslink

---

### Post by djsephiroth on 2011-12-06
From what I am seeing, it appears that the fake root is denied access to locations such as /etc in the pbuilder chroot. No idea why that would be though.

Using $(DESTDIR) in the copy operations caused the build process to attempt to place the files in, for example, /tmp/buildd/nameoftheprogram.1.2-3/etc/init.d/somedaemon (in the real fs, where "/tmp/buildd/nameoftheprogram.1.2-3" is the build dir) instead of /etc/init.d/somedaemon (in the chroot)

---

### Post by MG&amp;TL on 2011-12-06
> **djsephiroth said:**
> From what I am seeing, it appears that the fake root is denied access to locations such as /etc in the pbuilder chroot. No idea why that would be though.

Using $(DESTDIR) in the copy operations caused the build process to attempt to place the files in, for example, /tmp/buildd/nameoftheprogram.1.2-3/etc/init.d/somedaemon (in the real fs, where "/tmp/buildd/nameoftheprogram.1.2-3" is the build dir) instead of /etc/init.d/somedaemon (in the chroot)

That's good, all pbuilder does is emulate the build machines to make sure you don't waste time yourself. It needs to have write permissions so it can build the deb.

Basically, preappend $DESTDIR to all instances of output files.

---

### Post by djsephiroth on 2011-12-06
With $(DESTDIR), I get "no such file/directory" errors instead of "permission denied" errors.

---

### Post by MG&amp;TL on 2011-12-06
> **djsephiroth said:**
> With $(DESTDIR), I get "no such file/directory" errors instead of "permission denied" errors.

Weird. Build it locally before you build with pbuilder. You should end up with an entry in debian representing the file tree.

---

### Post by djsephiroth on 2011-12-07
Same "No such file or directory" errors when using dpkg-buildpackage locally instead of pbuilder.

```
cp: cannot create regular file `/home/office/nslink-4.28.1/debian/tmp/lib/modules/3.2.0-3-generic-pae/misc': No such file or directory
make[1]: *** [install] Error 1
dh_auto_install: make -j1 install DESTDIR=/home/office/nslink-4.28.1/debian/tmp returned exit code 2
make: *** [binary] Error 25
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2
```

---

### Post by MG&amp;TL on 2011-12-07
> **djsephiroth said:**
> Same "No such file or directory" errors when using dpkg-buildpackage locally instead of pbuilder.

```
cp: cannot create regular file `/home/office/nslink-4.28.1/debian/tmp/lib/modules/3.2.0-3-generic-pae/misc': No such file or directory
make[1]: *** [install] Error 1
dh_auto_install: make -j1 install DESTDIR=/home/office/nslink-4.28.1/debian/tmp returned exit code 2
make: *** [binary] Error 25
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2
```

If you're using cp (I think you're meant to use install, instead, but hey), I think a workaround would be to put a mkdir -p in front of every cp.

Or you could use debian/package.install and use dh_install.

---

### Post by djsephiroth on 2011-12-07
I may just cook up my own Makefile instead of using the one provided with the source. There were some other odd things aside from the "cp" commands.

---

### Post by djsephiroth on 2011-12-09
I resolved the issues by:

[LIST]
[*]Replacing "cp" and "chmod" operations with "install"
[*]Removing all "strip" operations
[*]Prepending $(DESTDIR)$(PREFIX) to all instances of absolute paths
[/LIST]

---

### Post by MG&amp;TL on 2011-12-09
> **djsephiroth said:**
> I resolved the issues by:

[LIST]
[*]Replacing "cp" and "chmod" operations with "install"
[*]Removing all "strip" operations
[*]Prepending $(DESTDIR)$(PREFIX) to all instances of absolute paths
[/LIST]

Good, good. Nice to hear you got it working, some of mine are a nightmare. Nice people like bachstelze and sevenmachines help though.

---

### Post by djsephiroth on 2011-12-09
Indeed, thanks for the assistance.

---

