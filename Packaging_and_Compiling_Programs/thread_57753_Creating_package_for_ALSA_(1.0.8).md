---
title: "Creating package for ALSA (1.0.8)"
date: 2005-08-17
forum: Packaging and Compiling Programs
---

### Post by gray-squirrel on 2005-08-17
I'm making a second attempt to install the ALSA driver for my SoundBlaster Live 24 card, using the method indicated here:

[http://www.ubuntuforums.org/showpost.php?p=90885&postcount=1](http://www.ubuntuforums.org/showpost.php?p=90885&postcount=1)


I used this method when I had the 386 kernel, but lost all sound after downloading the K7 kernel and removing the 386 kernel.  When I decided to get sound back on my machine, I tried to compile version 1.0.9 (as opposed to 1.0.8 ) and somehow all drives, save the hard disk drives, ceased working and I lost modem support (not to mention that sound did not come back), so I ended up reinstalling the K7 kernel image. 

This time, I followed the directions indicated above, but when I got to typing in [FONT=Courier New]sudo debian/rules binary_modules KSRC=/usr/src/linux-headers-$(uname -r)/ KVERS=$(uname -r)[/FONT], the computer gave the following output.

```

make[1]: Leaving directory `/usr/src/modules/alsa-driver'
/usr/bin/make  DESTDIR=/usr/src/modules/alsa-driver/debian/alsa-modules-_KVERS_ install-modules
make[1]: Entering directory `/usr/src/modules/alsa-driver'
find /usr/src/modules/alsa-driver/debian/alsa-modules-_KVERS_/lib/modules/2.6.10-5-k7/kernel/sound -name 'snd*.*o' | xargs rm -f
find: /usr/src/modules/alsa-driver/debian/alsa-modules-_KVERS_/lib/modules/2.6.10-5-k7/kernel/sound: No such file or directory
make[2]: Entering directory `/usr/src/modules/alsa-driver/acore'
mkdir -p /usr/src/modules/alsa-driver/debian/alsa-modules-_KVERS_/lib/modules/2.6.10-5-k7/kernel/sound/acore
cp snd-page-alloc.ko snd-pcm.ko snd-rtctimer.ko snd-timer.ko snd.ko /usr/src/modules/alsa-driver/debian/alsa-modules-_KVERS_/lib/modules/2.6.10-5-k7/kernel/sound/acore
make[3]: Entering directory `/usr/src/modules/alsa-driver/acore/oss'
mkdir -p /usr/src/modules/alsa-driver/debian/alsa-modules-_KVERS_/lib/modules/2.6.10-5-k7/kernel/sound/acore/oss
cp snd-mixer-oss.ko snd-pcm-oss.ko /usr/src/modules/alsa-driver/debian/alsa-modules-_KVERS_/lib/modules/2.6.10-5-k7/kernel/sound/acore/oss
make[3]: Leaving directory `/usr/src/modules/alsa-driver/acore/oss'
make[3]: Entering directory `/usr/src/modules/alsa-driver/acore/seq'
mkdir -p /usr/src/modules/alsa-driver/debian/alsa-modules-_KVERS_/lib/modules/2.6.10-5-k7/kernel/sound/acore/seq
cp snd-seq-device.ko snd-seq-midi-event.ko snd-seq.ko /usr/src/modules/alsa-driver/debian/alsa-modules-_KVERS_/lib/modules/2.6.10-5-k7/kernel/sound/acore/seq
make[4]: Entering directory `/usr/src/modules/alsa-driver/acore/seq/instr'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq/instr'
make[4]: Entering directory `/usr/src/modules/alsa-driver/acore/seq/oss'
mkdir -p /usr/src/modules/alsa-driver/debian/alsa-modules-_KVERS_/lib/modules/2.6.10-5-k7/kernel/sound/acore/seq/oss
cp snd-seq-oss.ko /usr/src/modules/alsa-driver/debian/alsa-modules-_KVERS_/lib/modules/2.6.10-5-k7/kernel/sound/acore/seq/oss
make[4]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq/oss'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/acore'
make[2]: Entering directory `/usr/src/modules/alsa-driver/i2c'
make[3]: Entering directory `/usr/src/modules/alsa-driver/i2c/other'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/i2c/other'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/i2c'
make[2]: Entering directory `/usr/src/modules/alsa-driver/drivers'
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl3'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl3'
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl4'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl4'
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/mpu401'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/mpu401'
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/vx'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/vx'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/drivers'
make[2]: Entering directory `/usr/src/modules/alsa-driver/isa'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/msnd'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/msnd'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1816a'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1816a'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1848'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1848'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/cs423x'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/cs423x'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/es1688'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/es1688'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/gus'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/gus'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/opti9xx'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/opti9xx'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/sb'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/sb'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/wavefront'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/wavefront'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/isa'
make[2]: Entering directory `/usr/src/modules/alsa-driver/synth'
make[3]: Entering directory `/usr/src/modules/alsa-driver/synth/emux'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/synth/emux'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/synth'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/pdplus'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/pdplus'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/azx'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/azx'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/pcxhr'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/pcxhr'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/echoaudio'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/echoaudio'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ac97'
mkdir -p /usr/src/modules/alsa-driver/debian/alsa-modules-_KVERS_/lib/modules/2.6.10-5-k7/kernel/sound/pci/ac97
cp snd-ac97-codec.ko /usr/src/modules/alsa-driver/debian/alsa-modules-_KVERS_/lib/modules/2.6.10-5-k7/kernel/sound/pci/ac97
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ac97'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ali5451'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ali5451'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/au88x0'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/au88x0'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ca0106'
mkdir -p /usr/src/modules/alsa-driver/debian/alsa-modules-_KVERS_/lib/modules/2.6.10-5-k7/kernel/sound/pci/ca0106
cp snd-ca0106.ko /usr/src/modules/alsa-driver/debian/alsa-modules-_KVERS_/lib/modules/2.6.10-5-k7/kernel/sound/pci/ca0106
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ca0106'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/cs46xx'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/cs46xx'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/emu10k1'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/emu10k1'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ice1712'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ice1712'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/korg1212'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/korg1212'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/mixart'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/mixart'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/nm256'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/nm256'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/rme9652'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/rme9652'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/trident'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/trident'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ymfpci'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ymfpci'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/vx222'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/vx222'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci'
make[2]: Entering directory `/usr/src/modules/alsa-driver/usb'
make[3]: Entering directory `/usr/src/modules/alsa-driver/usb/usx2y'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/usb/usx2y'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/usb'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pcmcia'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia'
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
dh_testdir
dh_testroot
dh_installdirs
dh_installchangelogs
bash -c "shopt -s nullglob ; dh_installdocs /usr/share/doc/alsa-source/copyright debian/changelog.*"
dh_strip
dh_compress
dh_fixperms
dh_installdeb
dh_shlibdeps
dh_gencontrol -- -v"1.0.8-4ubuntu4"
dh_md5sums
dh_builddeb --destdir=/usr/src/modules/alsa-driver/..
dpkg-deb: package name has characters that aren't lowercase alphanums or `-+.'
dh_builddeb: command returned error code 512

``` 

Although I know that a package could not be made because _KVERS_ was inserted when it should have been the kernel version number, I couldn't find out why the kernel version number would not be inserted in file names, as it is a variable.  I could not find anything wrong in the [FONT=Courier New]debian/rules[/FONT] file for the ALSA 1.0.8 driver.  I even used [FONT=Courier New]`uname -r`[/FONT] and the actual revision number, both in the command line and in debian/rules in an attempt to force the computer to put the version number in the file name, and it didn't work.

A couple of days ago I came across something that could have been very helpful.  I found that KVERS to be "empty" (by typing [FONT=Courier New]echo $KVERS[/FONT]), and that I could export the value ([FONT=Courier New]export KVERS=`uname -r`[/FONT]) so that the script could actually use something.  Somehow it appears [FONT=Courier New]debian/rules[/FONT] ignores it, and after I get the error message like the one above, KVERS is reset to a null string.

Here's the [FONT=Courier New]debian/rules file[/FONT], located in my [FONT=Courier New]usr/src/modules[/FONT]:

```

#!/usr/bin/make -f

# Written by Steve Kowalik <stevenk@debian.org> for the New Alsa-Source.
# Loosely based on the rules file from pcmcia-cs and the old alsa-source.

KSRC ?= /usr/src/linux
KDREV ?= unknown
KVERS ?= unknown

ifeq ($(KDEP),)
KDEPC =
else
KDEPC = $(KDEP),
endif

# See if we can work out the compiler used
ifeq ($(origin CC),default)
ifneq "$(wildcard $(KSRC)/include/linux/compile.h)" ""
CC = gcc-$(shell grep LINUX_COMPILER $(KSRC)/include/linux/compile.h | sed 's/.* \([0-9]\+\.[0-9]\+\).*/\1/')
else
CC = gcc
endif
endif

# Special case gcc 2.7.2
ifeq ($(CC),gcc-2.7)
CC = gcc272
endif

# If they didn't set $(KVERS), see if we can do it for them.
ifeq ($(KVERS),unknown)
ifneq "$(wildcard $(KSRC)/include/linux/version.h)" ""
KVERS = $(shell head -1 $(KSRC)/include/linux/version.h | sed 's/.*"\(.*\)"$$/\1/')
endif
endif

# Clear root command if already root
ifeq ($(shell id -u),0)
ROOT_CMD=
endif

# Use updates/ subdirectory so that the modules in alsa-modules-$KVERS
# are given priority (by depmod) over modules under kernel/.
CONFIGURE_OPT = --prefix=/usr \
		--with-kernel=$(KSRC) \
		--with-build=$(KSRC) \
		--with-moddir=/lib/modules/$(KVERS)/updates/alsa \
		--with-sequencer=yes

# See SF bug #550435
ifneq (,$(findstring 2.2.,$(KVERS)))
CONFIGURE_OPT += --disable-verbose-printk
endif

# Read in config file, generated by debconf.
ifeq (/etc/alsa/alsa-source.conf,$(wildcard /etc/alsa/alsa-source.conf))
include /etc/alsa/alsa-source.conf
endif
ifeq ($(HOME)/.alsa-source.conf,$(wildcard $(HOME)/.alsa-source.conf))
include $(HOME)/.alsa-source.conf
endif
ifeq ($(CURDIR)/debian/alsa-source.conf,$(wildcard $(CURDIR)/debian/alsa-source.conf))
include $(CURDIR)/debian/alsa-source.conf
endif

ifeq ($(ALSA_NOPNP),"y")
CONFIGURE_OPT += --with-isapnp=no
else
CONFIGURE_OPT += --with-isapnp=yes
endif

ifeq ($(ALSA_DEBUG),"y")
CONFIGURE_OPT += --with-debug=detect
endif

ifneq ($(ALSA_CARDS),"")
CONFIGURE_OPT += --with-cards=$(ALSA_CARDS)
endif

ifneq ($(ALSA_CARD_OPTIONS),"")
CONFIGURE_OPT += --with-card-options=$(ALSA_CARD_OPTIONS)
endif

ifneq ($(CONCURRENCY_LEVEL),)
MAKE_OPT = -j $(CONCURRENCY_LEVEL)
endif

VERSION = $(shell dpkg-parsechangelog | grep ^Vers | cut -d\  -f2)
ifneq ($(KDREV),unknown)
ifeq ($(findstring :,$(KDREV)),:)
VERSION := $(subst :,:$(VERSION)+,$(KDREV))
else
VERSION := $(VERSION)+$(KDREV)
endif
endif

echo-vars:
	@echo "I've been configured using:"
	@echo " - Kernel source of $(KSRC)"
	@echo " - Kernel version of $(KVERS)"
	@echo " - Kernel revision of $(KDREV)"
	@echo " - C compiler of $(CC)"
	@echo " - Make options of $(MAKE_OPT)"
	@echo " - Version of $(VERSION)"

configure: configure-stamp
configure-stamp:
	@if [ ! -x /usr/bin/$(CC) ]; then echo "You don't have the compiler that your kernel was built with installed"; exit 1; fi
	CC="$(CC)" ./configure $(CONFIGURE_OPT)
	touch configure-stamp

build: build-stamp
build-stamp: configure-stamp
	$(MAKE) $(MAKE_OPT) compile

install: install-stamp
install-stamp: build-stamp
	$(MAKE) $(MAKE_OPT) DESTDIR=$(CURDIR)/debian/$(shell dh_listpackages) install-modules

control-munge:
	for i in control preinst postinst postrm ; do \
		cp debian/$$i debian/$$i.old; \
		cat debian/$$i | sed -e 's/_KVERS_/$(KVERS)/g' -e 's/_KDEP_/$(KDEPC)/g' > debian/$$i.bak; \
		mv debian/$$i.bak debian/$$i; \
	done
	touch control-munge

clean-control-munge:
	for i in control preinst postinst postrm ; do \
		if [ -f debian/$$i.old ]; then \
			mv debian/$$i.old debian/$$i; \
		fi; \
	done
	-$(RM) control-munge

clean: clean-control-munge
	-make mrproper
	$(RM) configure-stamp
	$(RM) build-stamp

binary_modules: binary-modules
binary-modules: configure-stamp build-stamp control-munge install-stamp
	dh_testdir
	dh_testroot
	dh_installdirs
	dh_installchangelogs
	bash -c "shopt -s nullglob ; dh_installdocs /usr/share/doc/alsa-source/copyright debian/changelog.*"
	dh_strip
	dh_compress
	dh_fixperms
	dh_installdeb
	dh_shlibdeps
	dh_gencontrol -- -v"$(VERSION)"
	dh_md5sums 
ifeq "$(origin KPKG_DEST_DIR)" "undefined"
ifeq "$(origin KMAINT)" "undefined"
	dh_builddeb --destdir=$(CURDIR)/..
else
	dh_builddeb --destdir=$(KSRC)/..
endif
else
	dh_builddeb --destdir=$(KPKG_DEST_DIR)
endif

binary:
	@echo "Binary target not supported. Use binary-modules or make-kpkg."
	exit 1

# Targets that kernel-package uses.
kdist_configure: configure-stamp
kdist_config: configure-stamp
kdist_image:
	$(ROOT_CMD) $(MAKE) -f debian/rules binary-modules
	$(ROOT_CMD) $(MAKE) -f debian/rules clean
kdist_clean: clean
kdist:
	$(ROOT_CMD) $(MAKE) -f debian/rules binary-modules

.PHONY: configure build clean binary-modules binary_modules binary kdist_configure kdist_config kdist_image kdist_clean kdist

``` 

Is there something I'm overlooking which could actually get the source compiled into a package?

Many thanks in adavance for your help.

---

### Post by mazg on 2005-09-05
I have the same problem when I try to build the package. Have you found a solution yet?
Or can anybody else point me in the right direction?

---

### Post by mazg on 2005-09-06
Should have known........ It was as simple as doing:

```

apt-get remove alsa-source
apt-get install alsa-source

``` 

After that every thing seemed to go fine. :smile:

---

### Post by openmind on 2005-09-06
YESSSSS!!!

That was it! after weeks of trying; I*Have*Sound!! 

I've searched and tried everything on these forums (and elsewhere) and had almost given up. The reinstallation of the Alsa-source was it. I resignedly went back to alsamixer to "Unmute" for the thousandth time, but this time the speakers started to hiss! I can't explain the joy and relief I felt when I started to play a tune!!

Thank you.

---

### Post by gray-squirrel on 2005-09-20
I thought I had alsa-source deleted and reinstalled.  I'll check on this in the evening and post on what happens.  (It's been the first time in probably two weeks since I was on the forums, please forgive the delay in my reply.)

Thanks again.

---

### Post by gray-squirrel on 2005-09-20
I removed, then re-installed alsa-source, and then started the instructions from the beginning.  Here's what I have so far.

```
/usr/bin/make -C /usr/src/linux-source-2.6.10/ SUBDIRS=/usr/src/modules/alsa-driver O=/lib/modules/2.6.10-5-k7/build/ modules
make[2]: Entering directory `/usr/src/linux-source-2.6.10'
  CC [M]  /usr/src/modules/alsa-driver/acore/hwdep.o
In file included from include/linux/sched.h:191,
                 from include/linux/module.h:10,
                 from /usr/src/modules/alsa-driver/include/adriver.h:51,
                 from /usr/src/modules/alsa-driver/include/sound/driver.h:42,
                 from /usr/src/modules/alsa-driver/acore/hwdep.c:22:
include/linux/aio.h:151: error: field `wq' has incomplete type
In file included from include/linux/module.h:23,
                 from /usr/src/modules/alsa-driver/include/adriver.h:51,
                 from /usr/src/modules/alsa-driver/include/sound/driver.h:42,
                 from /usr/src/modules/alsa-driver/acore/hwdep.c:22:
include/asm/module.h:56:2: #error unknown processor family
In file included from /usr/src/modules/alsa-driver/include/adriver.h:587,
                 from /usr/src/modules/alsa-driver/include/sound/driver.h:42,
                 from /usr/src/modules/alsa-driver/acore/hwdep.c:22:
include/linux/pci.h:515: error: field `dev' has incomplete type
include/linux/pci.h:595: error: field `class_dev' has incomplete type
include/linux/pci.h:649: error: field `driver' has incomplete type
In file included from include/asm/pci.h:105,
                 from include/linux/pci.h:877,
                 from /usr/src/modules/alsa-driver/include/adriver.h:587,
                 from /usr/src/modules/alsa-driver/include/sound/driver.h:42,
                 from /usr/src/modules/alsa-driver/acore/hwdep.c:22:
include/asm-generic/pci-dma-compat.h: In function `pci_dma_supported':
include/asm-generic/pci-dma-compat.h:15: warning: implicit declaration of function `dma_supported'
include/asm-generic/pci-dma-compat.h: In function `pci_alloc_consistent':
include/asm-generic/pci-dma-compat.h:22: warning: implicit declaration of function `dma_alloc_coherent'
include/asm-generic/pci-dma-compat.h:22: warning: return makes pointer from integer without a cast
include/asm-generic/pci-dma-compat.h: In function `pci_free_consistent':
include/asm-generic/pci-dma-compat.h:29: warning: implicit declaration of function `dma_free_coherent'
include/asm-generic/pci-dma-compat.h: In function `pci_map_single':
include/asm-generic/pci-dma-compat.h:35: warning: implicit declaration of function `dma_map_single'
include/asm-generic/pci-dma-compat.h:35: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_unmap_single':
include/asm-generic/pci-dma-compat.h:42: warning: implicit declaration of function `dma_unmap_single'
include/asm-generic/pci-dma-compat.h:42: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_map_page':
include/asm-generic/pci-dma-compat.h:49: warning: implicit declaration of function `dma_map_page'
include/asm-generic/pci-dma-compat.h:49: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_unmap_page':
include/asm-generic/pci-dma-compat.h:56: warning: implicit declaration of function `dma_unmap_page'
include/asm-generic/pci-dma-compat.h:56: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_map_sg':
include/asm-generic/pci-dma-compat.h:63: warning: implicit declaration of function `dma_map_sg'
include/asm-generic/pci-dma-compat.h:63: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_unmap_sg':
include/asm-generic/pci-dma-compat.h:70: warning: implicit declaration of function `dma_unmap_sg'
include/asm-generic/pci-dma-compat.h:70: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_dma_sync_single_for_cpu':
include/asm-generic/pci-dma-compat.h:77: warning: implicit declaration of function `dma_sync_single_for_cpu'
include/asm-generic/pci-dma-compat.h:77: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_dma_sync_single_for_device':
include/asm-generic/pci-dma-compat.h:84: warning: implicit declaration of function `dma_sync_single_for_device'
include/asm-generic/pci-dma-compat.h:84: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_dma_sync_sg_for_cpu':
include/asm-generic/pci-dma-compat.h:91: warning: implicit declaration of function `dma_sync_sg_for_cpu'
include/asm-generic/pci-dma-compat.h:91: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_dma_sync_sg_for_device':
include/asm-generic/pci-dma-compat.h:98: warning: implicit declaration of function `dma_sync_sg_for_device'
include/asm-generic/pci-dma-compat.h:98: error: conversion to incomplete type
include/asm-generic/pci-dma-compat.h: In function `pci_dma_mapping_error':
include/asm-generic/pci-dma-compat.h:104: warning: implicit declaration of function `dma_mapping_error'
In file included from /usr/src/modules/alsa-driver/include/adriver.h:587,
                 from /usr/src/modules/alsa-driver/include/sound/driver.h:42,
                 from /usr/src/modules/alsa-driver/acore/hwdep.c:22:
include/linux/pci.h: In function `pci_get_drvdata':
include/linux/pci.h:970: warning: implicit declaration of function `dev_get_drvdata'
include/linux/pci.h:970: warning: return makes pointer from integer without a cast
include/linux/pci.h: In function `pci_set_drvdata':
include/linux/pci.h:975: warning: implicit declaration of function `dev_set_drvdata'
In file included from /usr/src/modules/alsa-driver/acore/hwdep.c:28:
/usr/src/modules/alsa-driver/include/sound/core.h: At top level:
/usr/src/modules/alsa-driver/include/sound/core.h:166: error: field `free_workq' has incomplete type
make[5]: *** [/usr/src/modules/alsa-driver/acore/hwdep.o] Error 1
make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[2]: *** [modules] Error 2
make[2]: Leaving directory `/usr/src/linux-source-2.6.10'
make[1]: *** [compile] Error 2
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make: *** [build-stamp] Error 2

``` 

I'm going to dig around and see what is going on.  I think something is missing from my system.  I don't have any old ALSA modules lingering around since they were removed on the last kernel update.

---

### Post by gray-squirrel on 2005-09-21
I think I know what happened.  It never occured to me that I may have to have kernel-source-2.4.27 installed as well.  I was notified that it would have to be if I wanted to install alsa-source via aptitude.  I declined because I didn't think it was necessary, since I have a 2.6.10 kernel and kernel source.  So I went ahead and used apt-get to download alsa-source.

Were any of you able to do this without kernel-source-2.4.27?  If so, I can see what else might be the cause.  Thanks again.

---

