---
title: "compiling a kernel module"
date: 2011-08-23
forum: Packaging and Compiling Programs
---

### Post by az20110303 on 2011-08-23
Hi! I need to learn to write kernel modules. I am using documentation from linux kernel source (file <linux_src>/Documentation/kbuild/modules.txt) and from TLDP project ([http://www.tldp.org/LDP/lkmpg/2.6/html/index.html](http://www.tldp.org/LDP/lkmpg/2.6/html/index.html))
I have pre-installed linux headers for my kernel. 
I created a directory with 2 files:

> az@az-ubuntu:/mnt/misc/code/my_module_2$ ls
hello.c  Makefile

az@az-ubuntu:/mnt/misc/code/my_module_2$ cat ./hello.c
/*  
 *  hello.c - The simplest kernel module.
 */
#include <linux/module.h>    /* Needed by all modules */
#include <linux/kernel.h>    /* Needed for KERN_INFO */

int init_module(void)
{
    printk(KERN_INFO "Hello world 1.\n");

    /* 
     * A non 0 return means init_module failed; module can't be loaded. 
     */
    return 0;
}

void cleanup_module(void)
{
    printk(KERN_INFO "Goodbye world 1.\n");
}

az@az-ubuntu:/mnt/misc/code/my_module_2$ cat ./Makefile
obj-m = hello.o
KVERSION = $(shell uname -r)
all:
        make -C /lib/modules/$(KVERSION)/build M=$(PWD)
clean:
        make -C /lib/modules/$(KVERSION)/build M=$(PWD) cleanLooks like I have done everything correct, but here's what happens when i try to make:

> az@az-ubuntu:/mnt/misc/code/my_module_2$ make
make: Nothing to be done for `all'.

the required directory with linux headers exists:

> az@az-ubuntu:/mnt/misc/code/my_module_2$ ls /lib/modules/`uname -r`/build
arch   crypto         drivers   fs       init  Kbuild   kernel  Makefile  Module.symvers  samples  security  source  ubuntu  virt
block  Documentation  firmware  include  ipc   Kconfig  lib     mm        net             scripts  sound     tools   usr 


Thanks for any help!

---

### Post by SevenMachines on 2011-08-23
Do you have tabs in front of those make commands in the Makefile? note

Your Makefile:
```
obj-m = hello.o
KVERSION = $(shell uname -r)
all:
make -C /lib/modules/$(KVERSION)/build M=$(PWD)
clean:
make -C /lib/modules/$(KVERSION)/build M=$(PWD) clean
``````
$ make
make: Nothing to be done for `all'.
```
Makefiles are sensitive to indentation....

New Makefile:
```
obj-m = hello.o
KVERSION = $(shell uname -r)
all:
  make -C /lib/modules/$(KVERSION)/build M=$(PWD)
clean:
  make -C /lib/modules/$(KVERSION)/build M=$(PWD) clean 

``````
$ make
make -C /lib/modules/3.0.0-9-generic/build M=/home/niall/Desktop/temp
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-9-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-9-generic'

```

---

### Post by az20110303 on 2011-08-23
[SevenMachines]("http://ubuntuforums.org/member.php?u=915690"), thanks you very much! Ofcourse I forgot about that "requirement" of Makefile!

---

