---
title: "Trying to build via82cxxx module"
date: 2008-12-28
forum: Programming Talk
---

### Post by 999alfred on 2008-12-28
When I upgraded to Hardy Heron my system got REAL SLOW and the problem was traced to the fact that the upgrade kernel. Look at the following

:/boot$ grep CONFIG_BLK_DEV_VIA82CXXX config*
config-2.6.17-10-generic:CONFIG_BLK_DEV_VIA82CXXX=m
config-2.6.17-11-generic:CONFIG_BLK_DEV_VIA82CXXX=m
config-2.6.17-12-generic:CONFIG_BLK_DEV_VIA82CXXX=m
config-2.6.24-21-generic:# CONFIG_BLK_DEV_VIA82CXXX is not set
config-2.6.24-22-generic:# CONFIG_BLK_DEV_VIA82CXXX is not set

Notice starting starting with the 2.6.24.xxx kernels the developers decided nobody needed to be using via 82cxxx chip sets.

So, now I am screwed. I must either build a whole new kernel or just the via82cxxx module. I decided to just try the just building the module.

I get the source code for 26.24.21-generic adn the such and did my research, finding a couple of posts concerning building modules. But, none of them work. Here is the gist.

:/boot$ ls /usr/src/linux-headers-2.6.24-21-generic/
arch    Documentation  include  Kbuild  Makefile        net      security
block   drivers        init     kernel  mm              samples  sound
crypto  fs             ipc      lib     Module.symvers  scripts  usr

So, that proves that the kernel header files exist.

I then tried this Makefile
KCFLAGS = -c -g -Wall -I/usr/src/linux-headers-2.6.24-21-generic/include -D__KERNEL__ -DMODULE
CC = gcc

M_OBJS = via82cxxx.o
M_TARGET = via82cxxx.ko

$(M_TARGET) : $(M_OBJS)
        ld -r -o $@ $(M_OBJS)

$(M_OBJS) : %.o : %.c
        $(CC) $(KCFLAGS) -o $@ $<

all: via82cxxx

clean:
        rm $(M_OBJS) *.log

and got the following output

gcc -c -g -Wall -I/usr/src/linux-headers-2.6.24-21-generic/include -D__KERNEL__ -DMODULE -o via82cxxx.o via82cxxx.c
In file included from /usr/src/linux-headers-2.6.24-21-generic/include/asm/processor.h:4,
                 from /usr/src/linux-headers-2.6.24-21-generic/include/linux/prefetch.h:14,
                 from /usr/src/linux-headers-2.6.24-21-generic/include/linux/list.h:8,
                 from /usr/src/linux-headers-2.6.24-21-generic/include/linux/module.h:9,
                 from via82cxxx.c:30:
/usr/src/linux-headers-2.6.24-21-generic/include/asm/processor_64.h:80: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/usr/src/linux-headers-2.6.24-21-generic/include/asm/processor_64.h:80: error: requested alignment is not a constant
/usr/src/linux-headers-2.6.24-21-generic/include/asm/processor_64.h:201: error: requested alignment is not a constant
In file included from /usr/src/linux-headers-2.6.24-21-generic/include/asm/ptrace.h:35,
                 from /usr/src/linux-headers-2.6.24-21-generic/include/asm/elf.h:8,
                 from /usr/src/linux-headers-2.6.24-21-generic/include/linux/elf.h:6,
                 from /usr/src/linux-headers-2.6.24-21-generic/include/linux/module.h:14,
                 from via82cxxx.c:30:
/usr/src/linux-headers-2.6.24-21-generic/include/asm/vm86.h:22:1: warning: "VM_MASK" redefined
In file included from /usr/src/linux-headers-2.6.24-21-generic/include/asm/processor.h:4,
                 from /usr/src/linux-headers-2.6.24-21-generic/include/linux/prefetch.h:14,
                 from /usr/src/linux-headers-2.6.24-21-generic/include/linux/list.h:8,
                 from /usr/src/linux-headers-2.6.24-21-generic/include/linux/module.h:9,
                 from via82cxxx.c:30:

the rest deleted.

So, then I tried this Makefile

 obj-m += via82cxxx.o

EXTRA_CFLAGS = -O2

all:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) modules

clean:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) clean
        $(RM) Module.markers modules.order

and got this
s$ make
make -C /lib/modules/`uname -r`/build M=/home/wd4nmq/linux/modules modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /home/wd4nmq/linux/modules/via82cxxx.o
/home/wd4nmq/linux/modules/via82cxxx.c:45:24: error: ide-timing.h: No such file or directory
/home/wd4nmq/linux/modules/via82cxxx.c:122: warning: ‘struct ide_timing’ declared inside parameter list
/home/wd4nmq/linux/modules/via82cxxx.c:122: warning: its scope is only this definition or declaration, which is probably not what you want
/home/wd4nmq/linux/modules/via82cxxx.c: In function ‘via_set_speed’:
/home/wd4nmq/linux/modules/via82cxxx.c:130: error: implicit declaration of function ‘FIT’
/home/wd4nmq/linux/modules/via82cxxx.c:130: error: dereferencing pointer to incomplete type
/home/wd4nmq/linux/modules/via82cxxx.c:135: error: dereferencing pointer to incomplete type
/home/wd4nmq/linux/modules/via82cxxx.c:135: error: dereferencing pointer to incomplete type
/home/wd4nmq/linux/modules/via82cxxx.c:138: error: dereferencing pointer to incomplete type
/home/wd4nmq/linux/modules/via82cxxx.c:138: error: dereferencing pointer to incomplete type
/home/wd4nmq/linux/modules/via82cxxx.c:141: error: dereferencing pointer to incomplete type
/home/wd4nmq/linux/modules/via82cxxx.c:141: error: dereferencing pointer to incomplete type
/home/wd4nmq/linux/modules/via82cxxx.c:142: error: dereferencing pointer to incomplete type
/home/wd4nmq/linux/modules/via82cxxx.c:142: error: dereferencing pointer to incomplete type
/home/wd4nmq/linux/modules/via82cxxx.c:143: error: dereferencing pointer to incomplete type
/home/wd4nmq/linux/modules/via82cxxx.c:143: error: dereferencing pointer to incomplete type
/home/wd4nmq/linux/modules/via82cxxx.c:144: error: dereferencing pointer to incomplete type
/home/wd4nmq/linux/modules/via82cxxx.c:144: error: dereferencing pointer to incomplete type
/home/wd4nmq/linux/modules/via82cxxx.c: In function ‘via_set_drive’:
/home/wd4nmq/linux/modules/via82cxxx.c:164: error: storage size of ‘t’ isn’t known
/home/wd4nmq/linux/modules/via82cxxx.c:164: error: storage size of ‘p’ isn’t known

So, how do I build this module alone so I can make my Ubuntu usable again?

tj

---

