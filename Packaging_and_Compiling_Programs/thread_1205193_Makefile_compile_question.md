---
title: "Makefile compile question"
date: 2009-07-05
forum: Packaging and Compiling Programs
---

### Post by VastOne on 2009-07-05
I am trying to get AMD K10 thermal sensors working in Jaunty using the following instructions

    $ mkdir k10temp && mv k10temp.c k10temp/k10temp.c

Create a makefile with the lines :

    obj-m := k10temp.o
    KDIR := /lib/modules/$(shell uname -r)/build
    PWD := $(shell pwd)

    default:

    $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

Example for my kernel is :

    obj-m := k10temp.o
    KDIR := /lib/modules/2.6.27.21-0.1-default/build
    PWD := $(shell pwd)
    default:
    $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

and now you can start compile these node with :

    $ make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
    $ cp k10temp.ko /lib/modules/$(uname -r)/kernel/drivers/hwmon
    $ depmod && modprobe k10temp

I know where it say (uname -r) I have to put in my own uname variables, but where there are other () such s (pwd) and (shell pwd) do I supply those variables as well?

First time compiling and using makefile, so please be gentle....

---

### Post by VastOne on 2009-07-06
> **VastOne said:**
> I am trying to get AMD K10 thermal sensors working in Jaunty using the following instructions

    $ mkdir k10temp && mv k10temp.c k10temp/k10temp.c

Create a makefile with the lines :

    obj-m := k10temp.o
    KDIR := /lib/modules/$(shell uname -r)/build
    PWD := $(shell pwd)

    default:

    $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

Example for my kernel is :

    obj-m := k10temp.o
    KDIR := /lib/modules/2.6.27.21-0.1-default/build
    PWD := $(shell pwd)
    default:
    $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

and now you can start compile these node with :

    $ make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
    $ cp k10temp.ko /lib/modules/$(uname -r)/kernel/drivers/hwmon
    $ depmod && modprobe k10temp

I know where it say (uname -r) I have to put in my own uname variables, but where there are other () such s (pwd) and (shell pwd) do I supply those variables as well?

First time compiling and using makefile, so please be gentle....

Bumpity Bump

---

### Post by VastOne on 2009-07-07
Bump

---

