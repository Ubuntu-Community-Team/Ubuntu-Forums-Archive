---
title: "programing kernel modules on Hoary"
date: 2005-04-24
forum: Programming Talk
---

### Post by czvak on 2005-04-24
Hi everyone,

recently i've been trying to compile some simple kernel modules on Hoary, but I get this error:

david@klendathu:~$ sudo insmod ./hello-2.ko
insmod: error inserting './hola-2.ko': -1 Invalid module format

or

david@klendathu:~$ sudo insmod hello-2.ko
insmod: error inserting 'hola-2.ko': -1 Invalid module format

The code of the module follows:

```
#include <linux/module.h>
#include <linux/kernel.h>
#include <linux/init.h>

static int __init hello_2_init(void)
{
        printk(KERN_ALERT "Hello world. \n");
        return 0;
}

static void __exit hello_2_exit(void)
{
        printk(KERN_ALERT "Goobye world. \n");
}

module_init(hello_2_init);
module_exit(hello_2_exit);

```

Any suggestions?, btw, i've installed modutils (of course), and the linux-restricted-modules. I don't know for sure if I need anything else.


Thanks.

---

### Post by toojays on 2005-04-24
What command are you using to compile this?

---

### Post by czvak on 2005-04-25
I use an standard Makefile:

obj-m += hello-1.o


And the compiling command is:

make -C /usr/src/linux-headers-2.6.10-5 SUBDIRS=$PWD modules

Where linux headers version corresponds to the kernel being used.

---

### Post by toojays on 2005-04-25
Sorry, but that works for me. You have changed the module name between your your first post and your last post, but apart from that, I don't see anything wrong.

---

### Post by czvak on 2005-04-25
But are you using a custom-compiled kernel or the one that comes with hoary. Because maybe i'm compiling a module using headers from a non existant (compiled) kernel.


Thanks.

---

### Post by toojays on 2005-04-25
Nope, this is the standard hoary kernel. Only difference is that mine is on powerpc, but that shouldn't matter.

---

