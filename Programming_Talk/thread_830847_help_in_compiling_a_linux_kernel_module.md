---
title: "help: in compiling a linux kernel module"
date: 2008-06-16
forum: Programming Talk
---

### Post by abhijeetnayak on 2008-06-16
I have created a hello.c module as:

#include <linux/init.h>
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

than i created a Makefile in same directory which contains:

obj-m := hello.o

then I try to compile it using the command 
make -C /usr/src/linux-headers-2.6.24-16 M=`pwd` modules

but there is no output file generated as hello.o . 
during the compilation it shows one error as: 
ERROR: Kernel configuration is invalid.
         include/linux/autoconf.h or include/config/auto.conf are missing.
         Run 'make oldconfig && make prepare' on kernel src to fix it.

please help me to solve this problem.
abhijeet nayak:confused:

---

### Post by abhijeetnayak on 2008-06-17
onyone help pls

---

