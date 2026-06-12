---
title: "make compling error"
date: 2013-01-30
forum: Programming Talk
---

### Post by raadyhere on 2013-01-30
I am trying to learn Kernel Module programming 

I made a simple hello.c program
#include<linux/init.h>
#include<linux/module.h>
static int hello_init(void){
printk(KERN_ALERT "Hello World");
return 0;
}
static void hello_exit(void){
printk(KERN_ALERT "Bye World");
}
module_init(hello_init);
module_exit(hello_exit);


I made a Makefile 

obj-m += hello.o
KDIR = /usr/src/linux-headers-3.5.0-17-generic
all:
    $(MAKE) -C $(KDIR) SUBDIR=$(PWD) modules
clean:
    rm -rf *.o *.ko *.mod.* *.symvers *.order


i executed it by command #make
I got the following error

raady@ubuntu:~/modulesprgm$ make
make -C /usr/src/linux-headers-3.5.0-17-generic SUBDIR=/home/raady/modulesprgm modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'
make[2]: *** No rule to make target  `/usr/src/linux-headers-3.5.0-17-generic/arch/x86/syscalls/syscall_32.tbl',  needed by `arch/x86/syscalls/../include/generated/asm/unistd_32.h'.   Stop.
make[1]: *** [archheaders] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic'
make: *** [all] Error 2





on commands # uname -r 
3.5.0-17-generic

on command : # ls /usr/src/linux-headers-3.5.0-17-generic

arch    Documentation  fs       ipc      kernel    mm              
samples   sound   ubuntu  block   drivers        
include  Kbuild   lib       Module.symvers  scripts   source  usr
crypto  firmware       init     Kconfig  Makefile  net             security  tools   virt


I cannot understand what is wrong, any help could be greatly appreciated 

according to documentation given make has to create hello.o file , but it doesnt and I couldnt go further

---

### Post by dwhitney67 on 2013-01-30
From what you have posted, it's not intuitive (at least for me) to discern what the root problem is with the errors that you are seeing.

One think I would recommend is that you correct your Makefile.  For starters, don't assume that the Linux Kernel header files are located in /usr/src.  This is not always the case on all Linux variants.  However, what is consistent is that the headers are location in /lib/modules.  (Of course, everything changes with time, so perhaps I'm wrong in making such a bold statement).

Also, I'm not familiar with the SUBDIR definition in your Makefile.

Change your Makefile to the following to see if you yield any better results:
```

obj-m := hello.o	# Module Name is hello.c

KDIR  := /lib/modules/$(shell uname -r)/build

all:
	$(MAKE) -C $(KDIR) M=$(PWD) modules

clean:
	$(MAKE) -C $(KDIR) M=$(PWD) clean
	$(RM) Module.markers modules.order

```
If this doesn't work, then perhaps you have yet to properly install the Linux Kernel Header File package.

---

### Post by raadyhere on 2013-02-01
Thanks a lot , its working ! so happy to see your reply !

---

