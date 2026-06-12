---
title: "My Module Demo"
date: 2005-06-13
forum: Programming Talk
---

### Post by daniminas on 2005-06-13
In kernel 2.6.10-5-385 , My modules: demo-module.c
----------------------------------------------------------
#include <linux/init.h>
#include <linux/module.h>

static int __init demo_init(void) {
        printk("initializing..\n");
        return 0;
}

static void __exit demo_exit(void) {
        printk("goodbye!\n");
}

module_init(demo_init);
module_exit(demo_exit);
MODULE_LICENSE("GPL");


---------------------------------------------------------------
# insmod demo-module.o
Error inserting 'demo-module.o': -1 Invalid module format

---------------------------------------------------------------

Insmod tells me "Invalid module format" and the kernel log says "No
module found in object".  

Someone can tell me what's trouble! ](*,) 

Thanks! Danielle

---

