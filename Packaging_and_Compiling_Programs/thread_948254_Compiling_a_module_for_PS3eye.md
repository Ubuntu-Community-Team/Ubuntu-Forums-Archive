---
title: "Compiling a module for PS3eye"
date: 2008-10-15
forum: Packaging and Compiling Programs
---

### Post by compeee2008 on 2008-10-15
Hi,

I've downloaded this ps3eye driver source from the [http://marc.info/?l=linux-video&m=121886284726264&w=2](http://marc.info/?l=linux-video&m=121886284726264&w=2) but I am having issues trying to compile and build it.

I try the following for my makefile:

obj-m := ov534.o
KDIR := /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)
default:
   $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules 

but get the following message:

make: Nothing to be done for `default'. 

I have installed kbuild and the following headers for 64 bit Heron Hardy:

linux-headers-2.6.24-19, linux-headers-2.6.24-19-generic, linux-headers-generic

Any ideas?

Paul

---

### Post by compeee2008 on 2008-10-16
Sorry guys,

I've copy the makefile from somewhere but the last line requires a tab.The problem is I get the following compilation error.

make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.build:41: /home/paul/Desktop/ps3eye/OV534/Makefile: No such file or directory
make[2]: *** No rule to make target `/home/paul/Desktop/ps3eye/OV534/Makefile'.  Stop.
make[1]: *** [_module_/home/paul/Desktop/ps3eye/OV534] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2

I don't understand the error message. Is it indicating that I don't have /home/paul/Desktop/ps3eye/OV534/Makefile directory in /usr/src/linux-headers-2.6.24-19-generic?
P

---

