---
title: "fatal error: linux/compiler.h: No such file or directory"
date: 2012-02-16
forum: Packaging and Compiling Programs
---

### Post by djsephiroth on 2012-02-16
I have a Makefile for a package that includes a kernel module. I just want to build the module. When I compile the target "all", which includes "modules", I have no problem. When I try to just compile "modules", I get this error:

```
$ cat /var/lib/dkms/nslink/4.28.1/build/make.log
DKMS make.log for nslink-4.28.1 for kernel 3.2.0-15-generic-pae (i686)
Thu Feb 16 08:50:01 CST 2012
Makefile:31: LINUX_VERSION: 3.2
Makefile:32: LINUX_SRC: /usr/src/linux-headers-3.2.0-15-generic-pae
cc    -c -o nslink.o nslink.c
nslink.c:87:28: fatal error: linux/compiler.h: No such file or directory
compilation terminated.
make: *** [nslink.o] Error 1
```

Here are the relevant parts of the Makefile:

```
# Retrieve the running kernel version
KVER=$(shell uname -r)

RM=rm -f
PWD:= $(shell pwd)
CURRENTDATE=$(shell date +%Y%m%d%H%M%S)

#  Find the kernel source/headers.
#  **** you, I know where it will always be
LINUX_SRC=/usr/src/linux-headers-$(KVER)

LINUX_VERSION=$(shell uname -r | awk '{ split($$0,a,"[.-]"); print a[1]"."a[2]}')

OLD_BUILD=no

ifeq ($(MAKELEVEL),0)
$(warning LINUX_VERSION: $(LINUX_VERSION))
$(warning LINUX_SRC: $(LINUX_SRC))
endif

obj-m += nslink.o

# build targetsfor 2.6, 3.x kernels
all:
	$(MAKE) -C $(LINUX_SRC) SUBDIRS=$(PWD) modules
	make CFLAGS=-Wall nslinkd
	make CFLAGS=-Wall nslinkadmin
	make CFLAGS=-Wall nslinkrelease

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

```

---

### Post by SevenMachines on 2012-02-16
```
$(MAKE) -C $(LINUX_SRC) SUBDIRS=$(PWD) modules
```What you're doing with this command is...
* -C, cd to the linux headers directory and run the makefile contained in that directory
* SUBDIRS is then passed to the makefile in LINUX_SRC to tell it that it should look in that directory for the source of the module its going to build

If you run 'make modules' directly then you're not moving to the LINUX_SRC makefile and getting it to build the module for you, its unlikely that 'fixing' that to work would make any sense in this context

---

### Post by djsephiroth on 2012-02-17
dkms.conf
```
PACKAGE_NAME="nslink"
PACKAGE_VERSION="4.28.1"
KERNELDIR="/lib/modules/${kernelver}/build"
INCLUDEDIR="/lib/modules/${kernelver}/build/include"
CLEAN="make clean"
BUILT_MODULE_NAME[0]="nslink"
BUILT_MODULE_LOCATION[0]="misc"
#MAKE[0]="cd ${dkms_tree}/nslink/4.28.1/build; make modules KERNEL_DIR=$kernel_source_dir KVERS=$kernelver"
MAKE[0]="make -C /usr/src/linux-headers-${kernelver} SUBDIRS=/usr/src/nslink-4.28.1 modules"
DEST_MODULE_LOCATION[0]="/kernel/drivers/misc"
AUTOINSTALL="yes"
REMAKE_INITRD="yes"

```

Results:
```
$ sudo dkms build -m nslink -v 4.28.1

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.2.0-16-generic-pae -C /usr/src/linux-headers-3.2.0-16-generic-pae SUBDIRS=/usr/src/nslink-4.28.1 modules.....
Error!  Build of nslink.ko failed for: 3.2.0-16-generic-pae (i686)
Consult the make.log in the build directory
/var/lib/dkms/nslink/4.28.1/build/ for more information.

```

$ cat /var/lib/dkms/nslink/4.28.1/build/make.log
```

DKMS make.log for nslink-4.28.1 for kernel 3.2.0-16-generic-pae (i686)
Fri Feb 17 09:46:42 CST 2012
make: Entering directory `/usr/src/linux-headers-3.2.0-16-generic-pae'
  CC [M]  /usr/src/nslink-4.28.1/nslink.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /usr/src/nslink-4.28.1/nslink.mod.o
  LD [M]  /usr/src/nslink-4.28.1/nslink.ko
make: Leaving directory `/usr/src/linux-headers-3.2.0-16-generic-pae'

```

Now I am really confused. The result of the make is an error, but when I cat the log, I do not see an error. This is probably just me being a noob, but I cannot tell what the error is.

---

### Post by Bachstelze on 2012-02-17
This looks like a bug in DKMS, You should probably ask on the DKMS mailing list

[https://lists.us.dell.com/mailman/listinfo/dkms-devel](https://lists.us.dell.com/mailman/listinfo/dkms-devel)

---

### Post by SevenMachines on 2012-02-18
Try passing --verbose as an arg to dkms, ie
```
$ dkms --verbose build -m nslink -v 4.28.1
```make.log showing no errors might not be an issue, the build may succeed and dkms fail. My guess would be something here
```
 BUILT_MODULE_LOCATION[0]="misc"
```is the .ko module actually in misc/ relative to the modules root source directory? With verbose you might see 'cannot find binary' or something like that if dkms can't actually locate the module its just built.
The lack of useful dkms log output is *definitely* a bug!

---

### Post by djsephiroth on 2012-02-20
Results of verbose:
```
$ sudo dkms --verbose build -m nslink -v 4.28.1

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
make clean
Makefile:31: LINUX_VERSION: 3.2
Makefile:32: LINUX_SRC: /usr/src/linux-headers-3.2.0-16-generic-pae
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

{ make KERNELRELEASE=3.2.0-16-generic-pae -C /usr/src/linux-headers-3.2.0-16-generic-pae SUBDIRS=/usr/src/nslink-4.28.1 modules; } >> /var/lib/dkms/nslink/4.28.1/build/make.log 2>&1

Error!  Build of nslink.ko failed for: 3.2.0-16-generic-pae (i686)
Consult the make.log in the build directory
/var/lib/dkms/nslink/4.28.1/build/ for more information.
```
Looks like... nothing in particular.

I'll send a message to the mailing list and see if that doesn't shed some more light on the issue. Thanks for the suggestion.

---

### Post by djsephiroth on 2012-02-22
Where should I file a bug? With Launchpad or upstream?

---

### Post by SevenMachines on 2012-02-22
Maybe give the dkms mailing list a go
[https://lists.us.dell.com/mailman/listinfo/dkms-devel](https://lists.us.dell.com/mailman/listinfo/dkms-devel)
Chances are that if its active then they will be the ones with the secret knowledge :)

---

### Post by djsephiroth on 2012-02-22
Nothing from the mailing list or the debian channel. I'll keep looking though. Tried changing a few things to see if I could get a clue as to what is happening, but no light has been shed.

---

### Post by SevenMachines on 2012-02-22
Obviously if you can post a link to the code, say on launchpad or something, its bound to improve the chance of someone seeing what's going wrong

---

### Post by djsephiroth on 2012-02-27
I seem to have not meditated sufficiently upon the sacred texts of Man Dkms, specifically the passage concerning "Dkms Dot'conf". It contains the story about how Dkms could not find a built module, but upon realizing that he could leave the built module field blank in the Dkms Dot'Conf, he was enlightened and suddenly knew precisely where the built module lay. Many debs were created and there was much rejoicing. Praise be to Mario Limonciello. Amen.

---

### Post by ngarong on 2012-02-27
Hi:

I'm also interested in rebuilding nslink. Any chance you can post your conf file? 

Thanks,

Tim

---

