---
title: "building module problem"
date: 2004-12-02
forum: Packaging and Compiling Programs
---

### Post by bluetechnx on 2004-12-02
Hello,

I am new to programming modules in Linux and have the following makefile provided for a Redhat distribution which compiles module source to modules.  I know that to do this I must have links to the source tree properly set for compiling.....the makefile provided that works at school is:

obj-m += mean_dev.o

KDIR := /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)

default:
        $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules
clean:
        rm -f *.ko *.o *.mod*


...but the kdir (kernel dir??) is not a path used by Ubuntu.  I have looked and tried to figure out where to point KDIR properly at to get some more work done away from school...but can't see where it should go...

Where should I point kdir to for a fresh install of Warty 4.10? ...any apt-gets needed ? ...I have "build-essential" packages on the system....

thanks for any help,

dg

---

### Post by Roptaty on 2004-12-02
Hello there.
You need to install the kernel headers corresponding to your kernel. 
For instance if you are running a 386 kernel: 
sudo apt-get install linux-headers-386
(change 386 with your kernel) 

The build link in /lib/modules/your kernel/ should then be set up properly by the linux-headers package. :)

---

### Post by bluetechnx on 2004-12-02
thank you!  :D

---

### Post by Pollywoggy on 2007-05-27
disregard

---

