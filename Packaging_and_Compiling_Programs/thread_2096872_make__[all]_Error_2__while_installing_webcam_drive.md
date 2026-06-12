---
title: "make: *** [all] Error 2  while installing webcam driver"
date: 2012-12-21
forum: Packaging and Compiling Programs
---

### Post by astarmathsandphysics on 2012-12-21
I am trying to install a driver for a philips spc900nc/00 webcam
I found the driver online via a link on the philips webset at

[http://saillard.org/linux/pwc/](http://saillard.org/linux/pwc/)

This is the full output when I try to compile the driver
/home/astarmathsandphysics/Desktop/pwc-10.0.12-rc1# make
make -C /lib/modules/3.0.0-17-generic-pae/build SUBDIRS=/home/astarmathsandphysics/Desktop/pwc-10.0.12-rc1 modules
make: *** /lib/modules/3.0.0-17-generic-pae/build: No such file or directory. Stop.
make: *** [all] Error 2

I have read a lot about linux headers but I don't think this is the problem. Instead I looked inside /lib/modules/3.0.0-17-generic-pae/ and can find nothing in the way of a build file or directory.
What can I do?

Am running ubuntu 12.04

---

### Post by fdrake on 2012-12-21
```

sudo apt-get install build-essential linux-generic* linux-headers-generic* linux-image-generic*

```

retry agan the make command

---

### Post by astarmathsandphysics on 2012-12-21
Did that and selected 'install maintainers version'
Installed with no errors but got same error message when I tried to compile the driver

I took a look inside the driver Makefile and found this

KVER  := $(shell uname -r)
KLINK := $(shell test -e /lib/modules/${KVER}/source/ && echo source || echo "build")
KSRC  := /lib/modules/$(KVER)/$(KLINK)
KMISC := /lib/modules/$(KVER)/kernel/drivers/usb/media
PWD := $(shell pwd)

If I edit this will that fix it?

---

### Post by fdrake on 2012-12-21
> **astarmathsandphysics said:**
> I took a look inside the driver Makefile and found this

KVER  := $(shell uname -r)
KLINK := $(shell test -e /lib/modules/${KVER}/source/ && echo source || echo "build")
KSRC  := /lib/modules/$(KVER)/$(KLINK)
KMISC := /lib/modules/$(KVER)/kernel/drivers/usb/media
PWD := $(shell pwd)

If I edit this will that fix it?
those are predefinted commands needed to search and configure the driver. what kind of errors do you get? The reasoin why you get errors it's because the make file cannot find the appropiate files for the setup.

---

### Post by astarmathsandphysics on 2012-12-21
This is the output, same as before. There is no file or output called build in /lib/modules/3.0.0-17-generic-pae/


/home/astarmathsandphysics/Desktop/pwc-10.0.12-rc1# make
make -C /lib/modules/3.0.0-17-generic-pae/build SUBDIRS=/home/astarmathsandphysics/Desktop/pwc-10.0.12-rc1 modules
make: *** /lib/modules/3.0.0-17-generic-pae/build: No such file or directory. Stop.
make: *** [all] Error 2

---

### Post by fdrake on 2012-12-21
it looks like we ddi not install the neccessary pack. try this and let me know
```

sudo apt-get install linux-generic-pae linux-headers-generic-pae linux-image-generic-pae

```

---

### Post by astarmathsandphysics on 2012-12-21
Tried that but I already have the latest version:

/home/astarmathsandphysics/Desktop/pwc-10.0.12-rc1# sudo apt-get install linux-generic-pae linux-headers-generic-pae linux-image-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-generic-pae is already the newest version.
linux-headers-generic-pae is already the newest version.
linux-image-generic-pae is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Nevertheless I tried my luck:


/home/astarmathsandphysics/Desktop/pwc-10.0.12-rc1# make
make -C /lib/modules/3.0.0-17-generic-pae/build SUBDIRS=/home/astarmathsandphysics/Desktop/pwc-10.0.12-rc1 modules
make: *** /lib/modules/3.0.0-17-generic-pae/build: No such file or directory. Stop.
make: *** [all] Error 2

same error

---

### Post by fdrake on 2012-12-21
we need to add the source path of the kernel manually. let's see what's yours
```
find /lib/modules/*generic | grep source 
```

---

### Post by astarmathsandphysics on 2012-12-21
System crashed. Might be a while

---

### Post by oldos2er on 2012-12-21
Moved to Packaging and Compiling Programs.

---

