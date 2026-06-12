---
title: "help required in compiling a kernel module"
date: 2011-07-28
forum: Packaging and Compiling Programs
---

### Post by pradhan.mcis on 2011-07-28
i wanted to try my hand at executing a very small module which is the  first example in Linux device Drivers by rubini. the contents of my  test. c are as follows:

[B]#include <linux/init.h>
#include <linux/module.h>
MODULE_LICENSE("Dual BSD/GPL");
static int hello_init(void)
{
    printk(KERN_ALERT "Hello, world\n");
    return 0;
}
static void hello_exit(void)
{
    printk(KERN_ALERT "Goodbye, cruel world\n");
}
module_init(hello_init);
module_exit(hello_exit);
[/B]
and i have created a Makefile with the following contents :

**obj -m := test.o**

when i try to give the command Make it says **"make: Nothing to be done for `test.c'.**


what might be the error???

---

### Post by SevenMachines on 2011-07-28
Try this makefile

Makefile:
```
obj-m += test.o

all:
  make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
  make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

``````
$ make

make -C /lib/modules/3.0.0-7-generic/build M=/home/seven/Desktop modules
cmake[1]: Entering directory `/usr/src/linux-headers-3.0.0-7-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-7-generic'

$ sudo insmod ./test.ko 
$ sudo rmmod test
$ dmesg | tail

[ 2133.824880] Hello, world
[ 2141.893531] Goodbye, cruel world

```

---

