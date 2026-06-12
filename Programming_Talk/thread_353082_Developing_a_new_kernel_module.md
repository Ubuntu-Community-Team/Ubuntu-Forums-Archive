---
title: "Developing a new kernel module"
date: 2007-02-04
forum: Programming Talk
---

### Post by yannifan on 2007-02-04
Hello ppl,
  Im new to kernel programming and have been trying to build my first kernel module 'hello world'

Im totally confused even after checking many posts. 

My source file is hello.c :
#include <linux/init.h>
#include <linux/module.h>
MODULE_LICENSE("Dual BSD/GPL");

static int hello_init(void)
{
	printk(KERN_ALERT "Hello World\n");
	return 0;
}
static int hello_exit(void)
{
	printk(KERN_ALERT "Goodbye!\n");
	return 0;
}
module_init(hello_init);
module_init(hello_exit);

I installed a kernel tree from kernel.org(2.6.18)
then i did "make config"
this is in /usr/src/linux-2.6.28.6

The Makefile addition is :

#Hello World module
obj-m += hello.ko
KDIR = /usr/src/linux-2.6.18.6/
SUBDIRS = $(PWD)
KVERSION = $(shell uname -r)
all:
	make	-C	/lib/modules/$(KVERSION)/build	M=$(PWD)	modules
clean:
	make	-C	/lib/modules/$(KVERSION)/build	M=$(PWD)	clean
modules:
	$(MAKE)	-C	$(KDIR)	M=$(SUBDIRS)	$@

Im not sure if this is correct (/lib/modules/2/6/15-27-386/build exists)
The source file is in /usr/src/linux*

Am i in the rite direction.... How do i continue???
Pls help

Cheers

PS: sorry if its a duplicate post couldnt help.

---

### Post by yannifan on 2007-02-04
I  forgot one more thing sorry
I have linuxheaders installed in /usr/src
ie. /usr/src/linux-headers-2.6.15-27
and linux-headers-2.6.15-27-386 exist

donno wat to do after tat!!!

---

### Post by lloyd mcclendon on 2007-02-04
one thing you'll definately want to do is get user mode linux up and running.  UML is a fake linux os that runs as a regular process.  if you make a mistake inside your module, you're going to be rebooting.  if you do it inside of UML, you just kill the process and start it up again.

i'm not sure what you're asking and it's been so long since i've done kernel development so i can't really tell you what to do.

---

