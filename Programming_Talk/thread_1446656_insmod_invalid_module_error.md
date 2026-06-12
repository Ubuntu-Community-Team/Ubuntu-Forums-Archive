---
title: "insmod :invalid module error"
date: 2010-04-04
forum: Programming Talk
---

### Post by scanty on 2010-04-04
hi all,
i am trying to get a simple module working

**_hello.c_**
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

**_Makefile_**
obj-m +=hello.o
all:
make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules


the module is created but not inserted.
I m using Ununtu 9.10 with kernel 2.6.33-020633-generic downloaded as deb file from ubuntu site ([http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/)).

Plzz help..

---

### Post by dwhitney67 on 2010-04-04
If the kernel module has indeed been built, then all you have to do next are the following
```

sudo insmod hello.ko
sudo rmmod hello

```
You can verify your module's output by examining /var/log/messages.


P.S.  You should not have had to download any kernel; the one your system uses is just fine.  All you would need, however, is the source (header files) for the running kernel.

---

### Post by scanty on 2010-04-04
> **dwhitney67 said:**
> If the kernel module has indeed been built, then all you have to do next are the following
```

sudo insmod hello.ko
sudo rmmod hello

```
You can verify your module's output by examining /var/log/messages.


P.S.  You should not have had to download any kernel; the one your system uses is just fine.  All you would need, however, is the source (header files) for the running kernel.

hi buddy,
the module is built but insmod gives the error i.e.**invalid module format**(using sudo).
i have also tried it on 2.6.31 kernel but getting the same error.
do you know any reason for it(like dependencies for kernel version and gcc etc)

---

