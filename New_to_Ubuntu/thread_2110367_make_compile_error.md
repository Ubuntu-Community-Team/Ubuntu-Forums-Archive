---
title: "make compile error"
date: 2013-01-30
forum: New to Ubuntu
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
make[2]: *** No rule to make target `/usr/src/linux-headers-3.5.0-17-generic/arch/x86/syscalls/syscall_32.tbl', needed by `arch/x86/syscalls/../include/generated/asm/unistd_32.h'.  Stop.
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

### Post by oldos2er on 2013-01-30
Closed, duplicate here: [http://ubuntuforums.org/showthread.php?t=2110369](http://ubuntuforums.org/showthread.php?t=2110369)
Please don't start more than one thread per question or problem, it dilutes community effort.

---

