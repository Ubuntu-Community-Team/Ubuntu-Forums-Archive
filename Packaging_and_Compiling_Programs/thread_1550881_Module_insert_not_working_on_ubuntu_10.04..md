---
title: "Module insert not working on ubuntu 10.04."
date: 2010-08-11
forum: Packaging and Compiling Programs
---

### Post by k210in on 2010-08-11
Hi,

    Here is a simple "hello world" module that i am trying to compile and load into the kernel. It compiles but am unable to load. Below are the module, Makefile and the command i am using to insert. 

---------------------------------------------------------------------------------------------
[COLOR=#000000] /*  
 *  hello-1.c - The simplest kernel module.
 */
#include <linux/module.h>	/* Needed by all modules */
#include <linux/kernel.h>	/* Needed for KERN_INFO */

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
}[/COLOR]----------------------------------------------------------------------------------------------

Am able to compile the above module with the following make file 

-------------------------------------------Makefile---------------------------------------
[COLOR=#000000]obj-m += hello-1.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean[/COLOR]
----------------------------------------------------------------------------------------------

But when i try inserting the .ko into the kernel i get the following error:

/work/my-drv$ insmod ./hello-1.ko 
insmod: error inserting './hello-1.ko': -1 Operation not permitted


What is going wrong here? Any help is really appreciated. The ubuntu version is 10.04.


Thanks
K

---

### Post by interval1066 on 2010-08-11
sudo insmod ./hello-1.ko perhaps?

---

### Post by k210in on 2010-08-11
Thanks.

---

