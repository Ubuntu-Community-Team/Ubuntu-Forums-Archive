---
title: "make and driver installation"
date: 2008-12-06
forum: Programming Talk
---

### Post by keithclark on 2008-12-06
I have a serial to usb adaptor and it came with linux drivers but I have no idea how to use them.

When I run make I get the following messages:

```

keithclark@keithclark-desktop:~/Documents/ftdi_sio$ make
gcc -Wall -D__KERNEL__ -DMODULE -I/lib/modules/2.6.27-7-generic/build/include -D__SMP__ -DSMP -DMODVERSIONS -include /lib/modules/2.6.27-7-generic/build/include/linux/modversions.h -I/usr/src/linux-2.6.27-7-generic/drivers/usb/serial/ -O   -c -o ftdi_sio.o ftdi_sio.c
cc1: error: /lib/modules/2.6.27-7-generic/build/include/linux/modversions.h: No such file or directory
In file included from /lib/modules/2.6.27-7-generic/build/include/linux/kernel.h:18,
                 from ftdi_sio.c:251:
/lib/modules/2.6.27-7-generic/build/include/linux/ratelimit.h: In function ‘ratelimit’:
/lib/modules/2.6.27-7-generic/build/include/linux/ratelimit.h:23: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.27-7-generic/build/include/linux/ratelimit.h:23: error: (Each undeclared identifier is reported only once
/lib/modules/2.6.27-7-generic/build/include/linux/ratelimit.h:23: error: for each function it appears in.)
In file included from /lib/modules/2.6.27-7-generic/build/include/asm/thread_info.h:22,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/thread_info.h:47,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/spinlock.h:50,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/mmzone.h:7,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/slab.h:12,
                 from ftdi_sio.c:254:
/lib/modules/2.6.27-7-generic/build/include/asm/processor.h: At top level:
/lib/modules/2.6.27-7-generic/build/include/asm/processor.h:112: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/lib/modules/2.6.27-7-generic/build/include/asm/processor.h:112: error: requested alignment is not a constant
In file included from /lib/modules/2.6.27-7-generic/build/include/asm/thread_info.h:22,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/thread_info.h:47,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/spinlock.h:50,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/mmzone.h:7,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/slab.h:12,
                 from ftdi_sio.c:254:
/lib/modules/2.6.27-7-generic/build/include/asm/processor.h:152:1: warning: "cache_line_size" redefined
In file included from /lib/modules/2.6.27-7-generic/build/include/asm/pda.h:7,
                 from /lib/modules/2.6.27-7-generic/build/include/asm/current.h:19,
                 from /lib/modules/2.6.27-7-generic/build/include/asm/processor.h:15,
                 from /lib/modules/2.6.27-7-generic/build/include/asm/thread_info.h:22,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/thread_info.h:47,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/spinlock.h:50,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/mmzone.h:7,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/slab.h:12,
                 from ftdi_sio.c:254:
/lib/modules/2.6.27-7-generic/build/include/linux/cache.h:64:1: warning: this is the location of the previous definition
/lib/modules/2.6.27-7-generic/build/include/asm/processor.h: In function ‘load_cr3’:
/lib/modules/2.6.27-7-generic/build/include/asm/processor.h:184: error: ‘CONFIG_PAGE_OFFSETUL’ undeclared (first use in this function)
/lib/modules/2.6.27-7-generic/build/include/asm/processor.h: At top level:
/lib/modules/2.6.27-7-generic/build/include/asm/processor.h:233: error: requested alignment is not a constant
/lib/modules/2.6.27-7-generic/build/include/asm/processor.h:270: error: requested alignment is not a constant
/lib/modules/2.6.27-7-generic/build/include/asm/processor.h: In function ‘wbinvd_halt’:
/lib/modules/2.6.27-7-generic/build/include/asm/processor.h:751: warning: implicit declaration of function ‘halt’
In file included from /lib/modules/2.6.27-7-generic/build/include/linux/mmzone.h:16,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/slab.h:12,
                 from ftdi_sio.c:254:
/lib/modules/2.6.27-7-generic/build/include/linux/nodemask.h: In function ‘__first_node’:
/lib/modules/2.6.27-7-generic/build/include/linux/nodemask.h:233: warning: implicit declaration of function ‘find_first_bit’
/lib/modules/2.6.27-7-generic/build/include/linux/nodemask.h: In function ‘__next_node’:
/lib/modules/2.6.27-7-generic/build/include/linux/nodemask.h:239: warning: implicit declaration of function ‘find_next_bit’
/lib/modules/2.6.27-7-generic/build/include/linux/nodemask.h: In function ‘__first_unset_node’:
/lib/modules/2.6.27-7-generic/build/include/linux/nodemask.h:257: warning: implicit declaration of function ‘find_first_zero_bit’
In file included from /lib/modules/2.6.27-7-generic/build/include/linux/termios.h:5,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/tty.h:11,
                 from ftdi_sio.c:255:
/lib/modules/2.6.27-7-generic/build/include/asm/termios.h: In function ‘kernel_termios_to_user_termio’:
/lib/modules/2.6.27-7-generic/build/include/asm/termios.h:79: warning: implicit declaration of function ‘__copy_to_user_ll’
In file included from /lib/modules/2.6.27-7-generic/build/include/linux/ktime.h:25,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/timer.h:5,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/workqueue.h:8,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/tty.h:12,
                 from ftdi_sio.c:255:
/lib/modules/2.6.27-7-generic/build/include/linux/jiffies.h:39:3: error: #error Invalid value of HZ.
/lib/modules/2.6.27-7-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-7-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-7-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-7-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-7-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-7-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-7-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-7-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-7-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-7-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-7-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-7-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-7-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-7-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-7-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-7-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
In file included from /lib/modules/2.6.27-7-generic/build/include/linux/elf.h:7,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/module.h:14,
                 from ftdi_sio.c:258:
/lib/modules/2.6.27-7-generic/build/include/asm/elf.h: In function ‘start_ia32_thread’:
/lib/modules/2.6.27-7-generic/build/include/asm/elf.h:153: warning: implicit declaration of function ‘load_gs_index’
/lib/modules/2.6.27-7-generic/build/include/asm/elf.h: In function ‘elf_common_init’:
/lib/modules/2.6.27-7-generic/build/include/asm/elf.h:166: error: ‘struct pt_regs’ has no member named ‘r8’
/lib/modules/2.6.27-7-generic/build/include/asm/elf.h:166: error: ‘struct pt_regs’ has no member named ‘r9’
/lib/modules/2.6.27-7-generic/build/include/asm/elf.h:166: error: ‘struct pt_regs’ has no member named ‘r10’
/lib/modules/2.6.27-7-generic/build/include/asm/elf.h:166: error: ‘struct pt_regs’ has no member named ‘r11’
/lib/modules/2.6.27-7-generic/build/include/asm/elf.h:167: error: ‘struct pt_regs’ has no member named ‘r12’
/lib/modules/2.6.27-7-generic/build/include/asm/elf.h:167: error: ‘struct pt_regs’ has no member named ‘r13’
/lib/modules/2.6.27-7-generic/build/include/asm/elf.h:167: error: ‘struct pt_regs’ has no member named ‘r14’
/lib/modules/2.6.27-7-generic/build/include/asm/elf.h:167: error: ‘struct pt_regs’ has no member named ‘r15’
In file included from /lib/modules/2.6.27-7-generic/build/include/linux/module.h:21,
                 from ftdi_sio.c:258:
/lib/modules/2.6.27-7-generic/build/include/asm/module.h:70:2: error: #error unknown processor family
In file included from /lib/modules/2.6.27-7-generic/build/include/linux/sched.h:77,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/interrupt.h:12,
                 from /lib/modules/2.6.27-7-generic/build/include/linux/usb.h:15,
                 from ftdi_sio.c:261:
/lib/modules/2.6.27-7-generic/build/include/linux/proportions.h: In function ‘prop_inc_percpu’:
/lib/modules/2.6.27-7-generic/build/include/linux/proportions.h:75: warning: implicit declaration of function ‘local_irq_save’
/lib/modules/2.6.27-7-generic/build/include/linux/proportions.h:77: warning: implicit declaration of function ‘local_irq_restore’
In file included from ftdi_sio.c:261:
/lib/modules/2.6.27-7-generic/build/include/linux/usb.h: In function ‘usb_register’:
/lib/modules/2.6.27-7-generic/build/include/linux/usb.h:1084: error: ‘KBUILD_MODNAME’ undeclared (first use in this function)
ftdi_sio.c: At top level:
ftdi_sio.c:655: error: unknown field ‘num_interrupt_in’ specified in initializer
ftdi_sio.c:656: error: unknown field ‘num_bulk_in’ specified in initializer
ftdi_sio.c:656: warning: missing braces around initializer
ftdi_sio.c:656: warning: (near initialization for ‘ftdi_sio_device.driver_list’)
ftdi_sio.c:656: warning: initialization makes pointer from integer without a cast
ftdi_sio.c:657: error: unknown field ‘num_bulk_out’ specified in initializer
ftdi_sio.c:657: warning: initialization makes pointer from integer without a cast
ftdi_sio.c:662: warning: initialization from incompatible pointer type
ftdi_sio.c:663: warning: initialization from incompatible pointer type
ftdi_sio.c:664: warning: initialization from incompatible pointer type
ftdi_sio.c:665: warning: initialization from incompatible pointer type
ftdi_sio.c:666: warning: initialization from incompatible pointer type
ftdi_sio.c:667: warning: initialization from incompatible pointer type
ftdi_sio.c:668: warning: initialization from incompatible pointer type
ftdi_sio.c:671: warning: initialization from incompatible pointer type
ftdi_sio.c:672: warning: initialization from incompatible pointer type
ftdi_sio.c:673: warning: initialization from incompatible pointer type
ftdi_sio.c:674: warning: initialization from incompatible pointer type
ftdi_sio.c:675: warning: initialization from incompatible pointer type
ftdi_sio.c: In function ‘update_mctrl’:
ftdi_sio.c:793: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c: In function ‘get_ftdi_divisor’:
ftdi_sio.c:878: error: ‘struct usb_serial_port’ has no member named ‘tty’
ftdi_sio.c:957: error: ‘struct usb_serial_port’ has no member named ‘tty’
ftdi_sio.c: In function ‘set_serial_info’:
ftdi_sio.c:1011: error: ‘struct usb_serial_port’ has no member named ‘tty’
ftdi_sio.c:1017: error: ‘struct usb_serial_port’ has no member named ‘tty’
ftdi_sio.c:1019: error: ‘struct usb_serial_port’ has no member named ‘tty’
ftdi_sio.c:1021: error: ‘struct usb_serial_port’ has no member named ‘tty’
ftdi_sio.c:1023: error: ‘struct usb_serial_port’ has no member named ‘tty’
ftdi_sio.c:1025: error: ‘struct usb_serial_port’ has no member named ‘tty’
ftdi_sio.c: In function ‘ftdi_determine_type’:
ftdi_sio.c:1105: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c: In function ‘ftdi_sio_port_probe’:
ftdi_sio.c:1277: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c: In function ‘ftdi_olimex_probe’:
ftdi_sio.c:1357: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c: In function ‘ftdi_open’:
ftdi_sio.c:1414: error: ‘struct usb_serial_port’ has no member named ‘tty’
ftdi_sio.c:1415: error: ‘struct usb_serial_port’ has no member named ‘tty’
ftdi_sio.c:1429: error: ‘struct usb_serial_port’ has no member named ‘tty’
ftdi_sio.c:1430: error: ‘struct usb_serial_port’ has no member named ‘tty’
ftdi_sio.c:1450: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c: In function ‘ftdi_close’:
ftdi_sio.c:1468: error: ‘struct usb_serial_port’ has no member named ‘tty’
ftdi_sio.c:1482: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c: In function ‘ftdi_write’:
ftdi_sio.c:1546: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c:1553: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c:1595: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c: In function ‘ftdi_chars_in_buffer’:
ftdi_sio.c:1701: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c: In function ‘ftdi_read_bulk_callback’:
ftdi_sio.c:1719: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c:1721: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c:1726: error: ‘struct usb_serial_port’ has no member named ‘open_count’
ftdi_sio.c:1729: error: ‘struct usb_serial_port’ has no member named ‘tty’
ftdi_sio.c:1742: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c: In function ‘ftdi_process_read’:
ftdi_sio.c:1782: error: ‘struct usb_serial_port’ has no member named ‘open_count’
ftdi_sio.c:1785: error: ‘struct usb_serial_port’ has no member named ‘tty’
ftdi_sio.c:1842: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c:1933: error: ‘struct usb_serial_port’ has no member named ‘open_count’
ftdi_sio.c:1946: error: ‘struct usb_serial_port’ has no member named ‘open_count’
ftdi_sio.c:1955: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c: In function ‘ftdi_break_ctl’:
ftdi_sio.c:1984: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c: In function ‘ftdi_set_termios’:
ftdi_sio.c:2001: error: ‘struct usb_serial_port’ has no member named ‘tty’
ftdi_sio.c:2016: error: ‘struct usb_serial_port’ has no member named ‘tty’
ftdi_sio.c:2053: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c:2066: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c:2077: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c:2084: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c:2102: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c:2129: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c:2141: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c: In function ‘ftdi_tiocmget’:
ftdi_sio.c:2166: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c:2185: error: expected ‘)’ before ‘KBUILD_MODNAME’
ftdi_sio.c: In function ‘ftdi_init’:
ftdi_sio.c:2329: error: expected ‘)’ before ‘KBUILD_MODNAME’
make: *** [ftdi_sio.o] Error 1
keithclark@keithclark-desktop:~/Documents/ftdi_sio$ 

```

Not sure where I'm going wrong here, or even how to begin troubleshooting it.

Below are some of the files included:



Here is the Makefile:

```

# This Makefile has been simplified as much as possible, by putting all
# generic material, independent of this specific directory, into
# ../Rules.make. Read that file for details

# The usb serial headers
INCLUDEUSBSER := $(shell echo "/usr/src/linux-`uname -r`/drivers/usb/serial/")

TOPDIR  := $(shell pwd)
#TOPDIR = .
include $(TOPDIR)/Rules.make

CFLAGS += -I$(INCLUDEUSBSER) -O

OBJS = ftdi.o

all: $(OBJS)

ftdi.o: ftdi_sio.o
	$(LD) -r $^ -o $@

install:
	install -d $(INSTALLDIR)
	install -c $(OBJS) $(INSTALLDIR)

clean:
	rm -f *.o *~ core


```

Here is the Rules.make file:

```

# -*-makefile-*-
#
# This file is part of the sample code for the book "Linux Device Drivers",
# second edition. It is meant to be generic and is designed to be recycled
# by other drivers. The comments should be clear enough.
# It partly comes from Linux Makefile, and needs GNU make. <rubini@linux.it>

# TOPDIR is declared by the Makefile including this file.
ifndef TOPDIR
	TOPDIR = .
endif

# KERNELDIR can be speficied on the command line or environment
ifndef KERNELDIR
	KERNELDIR := $(shell echo "/lib/modules/`uname -r`/build")
endif
# The headers are taken from the kernel
	INCLUDEDIR = $(KERNELDIR)/include

# We need the configuration file, for CONFIG_SMP and possibly other stuff
# (especiall for RISC platforms, where CFLAGS depends on the exact
# processor being used).
ifeq ($(KERNELDIR)/.config,$(wildcard $(KERNELDIR))/.config)
	include $(KERNELDIR)/.config
else
	MESSAGE := $(shell echo "WARNING: no .config file in $(KERNELDIR)")
endif

# ARCH can be speficed on the comdline or env. too, and defaults to this arch
# Unfortunately, we can't easily extract if from kernel configuration
# (well, we could look athe asm- symlink... don't know if worth the effort)
ifndef ARCH
  ARCH := $(shell uname -m | sed -e s/i.86/i386/ -e s/sun4u/sparc64/ \
		-e s/arm.*/arm/ -e s/sa110/arm/)
endif

# This is useful if cross-compiling. Taken from kernel Makefile (CC changed)
AS      =$(CROSS_COMPILE)as
LD      =$(CROSS_COMPILE)ld
CC      =$(CROSS_COMPILE)gcc
CPP     =$(CC) -E
AR      =$(CROSS_COMPILE)ar
NM      =$(CROSS_COMPILE)nm
STRIP   =$(CROSS_COMPILE)strip
OBJCOPY =$(CROSS_COMPILE)objcopy
OBJDUMP =$(CROSS_COMPILE)objdump

# The platform-specific Makefiles include portability nightmares.
# Some platforms, though, don't have one, so check for existence first
ARCHMAKEFILE = $(TOPDIR)/Makefile.$(ARCH)
ifeq ($(ARCHMAKEFILE),$(wildcard $(ARCHMAKEFILE)))
  include $(ARCHMAKEFILE)
endif

USBDI=/linux

# CFLAGS: all assignments to CFLAGS are inclremental, so you can specify
# the initial flags on the command line or environment, if needed.

	CFLAGS +=  -Wall -D__KERNEL__ -DMODULE -I$(INCLUDEDIR)

ifdef CONFIG_SMP
	CFLAGS += -D__SMP__ -DSMP
endif

# Prepend modversions.h if we're running with versioning.
ifdef CONFIG_MODVERSIONS
	CFLAGS += -DMODVERSIONS -include $(KERNELDIR)/include/linux/modversions.h
endif

#Install dir
VERSIONFILE = $(INCLUDEDIR)/linux/version.h
VERSION     = $(shell awk -F\" '/REL/ {print $$2}' $(VERSIONFILE))
INSTALLDIR = /lib/modules/$(VERSION)/misc


```

---

### Post by dwhitney67 on 2008-12-06
Where did you get the Makefile and the Rules.make from?  Seems a bit overcomplicated for compiling a single kernel device driver.

Plus this statement is not portable:
```

INCLUDEUSBSER := $(shell echo "/usr/src/linux-`uname -r`/drivers/usb/serial/")

```
It probably should be:
```

INCLUDEUSBSER := $(shell echo "/lib/modules/`uname -r`/build/drivers/usb/serial/")

```
Aside from that, the only other issue I can think of is that maybe you do not have the kernel development files installed; but this seems highly unlikely.

---

### Post by keithclark on 2008-12-06
I got these files straight from the supplier.

I changed as recommended and still a ton of errors.

Keith

---

### Post by dwhitney67 on 2008-12-06
Within your working directory (i.e. where the files the vendor supplied you), what files do you have?

---

### Post by keithclark on 2008-12-06
ftdi_sio.c
ftdi_sio.h
Makefile
Rules.make

---

### Post by dwhitney67 on 2008-12-06
Create a backup of your existing Makefile, and replace with this one:

```

SRCS    = ftdi_sio.c
OBJS    = $(SRCS:.c=.o)

obj-m  += $(OBJS)

CFLAGS += -I./


all:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) modules

clean:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) clean
        $(RM) Module.markers modules.order

```
This Makefile will not install anything, and in fact I do not even know if it will work.  But give it a shot.  If all works well, there should be an ftdi_sio.ko (kernel object) file in your present working directory.

P.S.  Note that with Makefiles, the indented statements are done with a single tab, and not spaces.

---

### Post by keithclark on 2008-12-06
keithclark@keithclark-desktop:~/Documents/ftdi_sio$ make
make -C /lib/modules/`uname -r`/build M=/home/keithclark/Documents/ftdi_sio modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/keithclark/Documents/ftdi_sio/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/keithclark/Documents/ftdi_sio] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [all] Error 2

---

### Post by dwhitney67 on 2008-12-06
Change the CFLAGS in the Makefile I supplied you to EXTRA_CFLAGS.

---

### Post by keithclark on 2008-12-06
keithclark@keithclark-desktop:~/Documents/ftdi_sio$ make
make -C /lib/modules/`uname -r`/build M=/home/keithclark/Documents/ftdi_sio modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/keithclark/Documents/ftdi_sio/ftdi_sio.o
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:655: error: unknown field ‘num_interrupt_in’ specified in initializer
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:656: error: unknown field ‘num_bulk_in’ specified in initializer
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:656: warning: missing braces around initializer
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:656: warning: (near initialization for ‘ftdi_sio_device.driver_list’)
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:656: warning: initialization makes pointer from integer without a cast
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:657: error: unknown field ‘num_bulk_out’ specified in initializer
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:657: warning: initialization makes pointer from integer without a cast
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:662: warning: initialization from incompatible pointer type
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:663: warning: initialization from incompatible pointer type
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:664: warning: initialization from incompatible pointer type
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:665: warning: initialization from incompatible pointer type
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:666: warning: initialization from incompatible pointer type
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:667: warning: initialization from incompatible pointer type
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:668: warning: initialization from incompatible pointer type
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:671: warning: initialization from incompatible pointer type
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:672: warning: initialization from incompatible pointer type
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:673: warning: initialization from incompatible pointer type
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:674: warning: initialization from incompatible pointer type
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:675: warning: initialization from incompatible pointer type
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c: In function ‘get_ftdi_divisor’:
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:878: error: ‘struct usb_serial_port’ has no member named ‘tty’
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:957: error: ‘struct usb_serial_port’ has no member named ‘tty’
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c: In function ‘set_serial_info’:
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:1011: error: ‘struct usb_serial_port’ has no member named ‘tty’
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:1017: error: ‘struct usb_serial_port’ has no member named ‘tty’
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:1019: error: ‘struct usb_serial_port’ has no member named ‘tty’
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:1021: error: ‘struct usb_serial_port’ has no member named ‘tty’
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:1023: error: ‘struct usb_serial_port’ has no member named ‘tty’
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:1025: error: ‘struct usb_serial_port’ has no member named ‘tty’
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c: In function ‘ftdi_open’:
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:1414: error: ‘struct usb_serial_port’ has no member named ‘tty’
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:1415: error: ‘struct usb_serial_port’ has no member named ‘tty’
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:1429: error: ‘struct usb_serial_port’ has no member named ‘tty’
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:1430: error: ‘struct usb_serial_port’ has no member named ‘tty’
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c: In function ‘ftdi_close’:
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:1468: error: ‘struct usb_serial_port’ has no member named ‘tty’
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c: In function ‘ftdi_read_bulk_callback’:
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:1726: error: ‘struct usb_serial_port’ has no member named ‘open_count’
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:1729: error: ‘struct usb_serial_port’ has no member named ‘tty’
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c: In function ‘ftdi_process_read’:
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:1782: error: ‘struct usb_serial_port’ has no member named ‘open_count’
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:1785: error: ‘struct usb_serial_port’ has no member named ‘tty’
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:1933: error: ‘struct usb_serial_port’ has no member named ‘open_count’
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:1946: error: ‘struct usb_serial_port’ has no member named ‘open_count’
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c: In function ‘ftdi_set_termios’:
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:2001: error: ‘struct usb_serial_port’ has no member named ‘tty’
/home/keithclark/Documents/ftdi_sio/ftdi_sio.c:2016: error: ‘struct usb_serial_port’ has no member named ‘tty’
make[2]: *** [/home/keithclark/Documents/ftdi_sio/ftdi_sio.o] Error 1
make[1]: *** [_module_/home/keithclark/Documents/ftdi_sio] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [all] Error 2

---

### Post by WhiskeyTangoFoxtrot on 2009-03-19
i would like to know the solution to this as well. I am encountering a similar problem while trying to install AODV routing protocol for the Ubuntu kernel. I take it this issue has something to do with the kernel and not the makefile since the software I am trying to install is completely different.

---

### Post by dwhitney67 on 2009-03-19
> **WhiskeyTangoFoxtrot said:**
> i would like to know the solution to this as well. I am encountering a similar problem while trying to install AODV routing protocol for the Ubuntu kernel. I take it this issue has something to do with the kernel and not the makefile since the software I am trying to install is completely different.

As I pointed out in one of my earlier posts, the linux header files are not always installed in /usr/src.  It can be installed in a different location... or in some cases, not at all (but this is rare).  Thus the Makefile may not be portable.

The defacto location to look for the source code is in /lib/modules/`uname -r`/build.

On an Ubuntu system, the linux header files are in /usr/src/linux-headers-`uname -r`, but that is the choice of Ubuntu; it may not be applicable to another distro.

As for the issues you are having, I cannot comment on them without seeing the errors as generated by the make process.

P.S.  Woohoo!  I have now made 2500 posts!

---

