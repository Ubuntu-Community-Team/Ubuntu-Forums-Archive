---
title: "Need help in compilin kernel modules"
date: 2008-01-29
forum: Packaging and Compiling Programs
---

### Post by driplock on 2008-01-29
i'm quite new to linux kernel module programming so i tried to do the basic helloworld module...but i have some problems with compiling it..

Here are some of the error message... please advise

gcc-3.3 -O2 -DMODULE -D__KERNEL__ -W -Wall -Wstrict-prototypes -Wmissing-prototypes -isystem /lib/modules/`uname -r`/build/include   -c -o modex1.o modex1.c
In file included from /lib/modules/2.6.20-16-generic/build/include/asm/thread_info.h:16,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/thread_info.h:21,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:9,
                 from modex1.c:3:
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h:82: error: `CONFIG_X86_L1_CACHE_SHIFT' undeclared here (not in a function)
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h:82: error: requested alignment is not a constant
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/list.h:8,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:10,
                 from modex1.c:3:
/lib/modules/2.6.20-16-generic/build/include/linux/prefetch.h: In function `prefetch_range':
/lib/modules/2.6.20-16-generic/build/include/linux/prefetch.h:64: error: `CONFIG_X86_L1_CACHE_SHIFT' undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/prefetch.h:64: error: (Each undeclared identifier is reported only once
/lib/modules/2.6.20-16-generic/build/include/linux/prefetch.h:64: error: for each function it appears in.)
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/sched.h:51,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/utsname.h:35,
                 from /lib/modules/2.6.20-16-generic/build/include/asm/elf.h:12,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/elf.h:7,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:15,
                 from modex1.c:3:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:33:3: #error You lose.
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:269:46: division by zero in #if
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/sched.h:51,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/utsname.h:35,
                 from /lib/modules/2.6.20-16-generic/build/include/asm/elf.h:12,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/elf.h:7,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:15,

---

### Post by driplock on 2008-01-29
i think i found a way to compile the module..however can anyone help me put this line:

$ make -C /lib/modules/$(uname -r)/build M=$(pwd) modules

on the makefile..so that i dont have to type the whole thing in the command line

---

### Post by driplock on 2008-02-01
Anyone who can help me please...

i tried this one:

obj-m :=modex2.o

    KDIR        := /lib/modules/$(shell uname -r)/build
    PWD         := $(shell pwd)

default:        
       $(MAKE) -C $(KDIR) M=$(PWD) 


but it gives me:

make: Nothing to be done for `default'.

when i do a "make"...

---

### Post by JamesUser on 2008-02-02
There doesn't seem to be anything wrong with ur makefile. Are you sure you have the linux-headers in the right place?

You can start with this guide, I suppose. [http://www.linuxdevcenter.com/pub/a/linux/2007/07/05/devhelloworld-a-simple-introduction-to-device-drivers-under-linux.html](http://www.linuxdevcenter.com/pub/a/linux/2007/07/05/devhelloworld-a-simple-introduction-to-device-drivers-under-linux.html)

---

