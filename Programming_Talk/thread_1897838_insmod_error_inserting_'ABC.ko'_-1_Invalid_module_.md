---
title: "insmod: error inserting 'ABC.ko': -1 Invalid module format"
date: 2011-12-20
forum: Programming Talk
---

### Post by Gurmeet Singh on 2011-12-20
Hi,

I am newbie to Linux. I have successfully compiled the linux source and also my own module but now i am facing the problem of loading the module.

my code id
> 
#include <linux/module.h>       /* Needed by all modules */
#include <linux/kernel.h>       /* Needed for KERN_INFO */
#include <linux/init.h>         /* Needed for the macros */

static int __init hello_start(void)
{
    printk(KERN_ALERT "Loading hello module...\n");
    printk(KERN_INFO "Hello world\n");
    return 0;
}

static void __exit hello_end(void)
{
    printk(KERN_INFO "Goodbye Mr.\n");
}

module_init(hello_start);
module_exit(hello_end);


after executing the command " make -C /usr/src/linux-3.0 M=$(pwd) modules"
it successfully compiles the module.
> 
make: Entering directory `/usr/src/linux-3.0'
  CC [M]  /home/administrator/Desktop/Developement/hello.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/administrator/Desktop/Developement/hello.mod.o
  LD [M]  /home/administrator/Desktop/Developement/hello.ko
make: Leaving directory `/usr/src/linux-3.0'


but when i issue command "sudo insmod hello.ko".
it is giving error as "**insmod: error inserting 'hello.ko': -1 Invalid module format**".

I have googled through net but nothing found helpful.
Please provide me the expert guide.
thanks.

---

