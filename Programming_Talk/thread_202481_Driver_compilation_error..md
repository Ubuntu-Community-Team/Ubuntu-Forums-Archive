---
title: "Driver compilation error."
date: 2006-06-23
forum: Programming Talk
---

### Post by brasbril on 2006-06-23
Hello all,

 I'm trying to compile a driver (for a dwl-g122 rev C. usb wireless "card") and I'm not able to. The installation is new, I've apt-getted the linux-headers, linux-source and build-essentials. First of all I had problems with the /lib/modules/2.6.15-25-server/build directory but this is solved. Now the problems are the following:


make -C /lib/modules/2.6.15-25-server/build SUBDIRS=/home/albert/RT73_Linux_STA_Drv1.0.3.0/Module modules
make[1]: Entering directory `/usr/src/linux-source-2.6.15'
Makefile:490: .config: No such file or directory

  WARNING: Symbol version dump /usr/src/linux-source-2.6.15/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/albert/RT73_Linux_STA_Drv1.0.3.0/Module/rtmp_main.o
cc1: error: include/linux/autoconf.h: No such file or directory
In file included from include/linux/module.h:9,
                 from /home/albert/RT73_Linux_STA_Drv1.0.3.0/Module/rt_config.h:63,
                 from /home/albert/RT73_Linux_STA_Drv1.0.3.0/Module/rtmp_main.c:40:
include/linux/config.h:6:28: error: linux/autoconf.h: No such file or directory
In file included from include/linux/module.h:10,
                 from /home/albert/RT73_Linux_STA_Drv1.0.3.0/Module/rt_config.h:63,
                 from /home/albert/RT73_Linux_STA_Drv1.0.3.0/Module/rtmp_main.c:40:

And it continues with lines and lines of warnings and errors. I don't know what do I need to do or what is misconfigured. I'm no newby to programming but I am newby for everything that has to do with linux system compilations. If someone had had the same troubles and knows what to do...thanks a lot,

A.

---

### Post by peterthewolf on 2006-06-27
Similar situation but get following error

peter@peter-desktop:~$ dir
Desktop  Examples  RT73_Linux_STA_Drv1.0.3.0
peter@peter-desktop:~$ cd RT73_Linux_STA_Drv1.0.3.0
peter@peter-desktop:~/RT73_Linux_STA_Drv1.0.3.0$ cd Module
peter@peter-desktop:~/RT73_Linux_STA_Drv1.0.3.0/Module$ make all
make -C /lib/modules/2.6.15-23-386/build SUBDIRS=/home/peter/RT73_Linux_STA_Drv1.0.3.0/Module modules
make[1]: Entering directory `/lib/modules/2.6.15-23-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-23-386/build'
make: *** [all] Error 2
peter@peter-desktop:~/RT73_Linux_STA_Drv1.0.3.0/Module$ make all
make -C /lib/modules/2.6.15-23-386/build SUBDIRS=/home/peter/RT73_Linux_STA_Drv1.0.3.0/Module modules
make[1]: Entering directory `/lib/modules/2.6.15-23-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-23-386/build'
make: *** [all] Error 2
peter@peter-desktop:~/RT73_Linux_STA_Drv1.0.3.0/Module$

What is the meaning of
make[1]: *** No rule to make target `modules'.  Stop.

---

