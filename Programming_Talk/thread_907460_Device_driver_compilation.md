---
title: "Device driver compilation"
date: 2008-09-01
forum: Programming Talk
---

### Post by rajez79 on 2008-09-01
Am getting the follwing error while compiling a device driver program

rajesh@rajesh-desktop:~/Desktop$ gcc dd.c
dd.c:1:24: error: linux/init.h: No such file or directory
dd.c:2:26: error: linux/module.h: No such file or directory

Please help me in solving this....

---

### Post by xeth_delta on 2008-09-01
> **rajez79 said:**
> Am getting the follwing error while compiling a device driver program

rajesh@rajesh-desktop:~/Desktop$ gcc dd.c
dd.c:1:24: error: linux/init.h: No such file or directory
dd.c:2:26: error: linux/module.h: No such file or directory

Please help me in solving this....

What exactly are you trying to compile? The errors mean that you need to install the linux kernel headers for your kernel version. To find out your kernel version:
```
uname -r
```
search for headers with synaptic, adept, apt-cache/apt-get or aptitude and install them. It should compile afterwards.

---

### Post by rajez79 on 2008-09-02
> **xeth_delta said:**
> What exactly are you trying to compile? The errors mean that you need to install the linux kernel headers for your kernel version. To find out your kernel version:
```
uname -r
```
search for headers with synaptic, adept, apt-cache/apt-get or aptitude and install them. It should compile afterwards.

Hi,

This is the prg i tried of compiling, as a start to device driver programming. if it gets compiled i thought of inserting it into the kernel using "insmod" and check using "dmesg".

#include <linux/init.h>
#include <linux/module.h>

static int init_module(void)
{
	printk("Init Module\n");
	return (0);
}

static void cleanup_module(void)
{
	printk("Cleanup Module\n");
}

I checked the /usr/src, the kernel headers are there but after giving the full path like

#include </usr/src/linux-headers-2.6.20-15/include/linux/init.h>
#include </usr/src/linux-headers-2.6.20-15/include/linux/module.h>

instead of giving #include <linux/init.h> or <linux/module.h>

i can able to compile the code but with a lot of errors. Do you any kernel versions which works fine....

---

### Post by rajez79 on 2008-09-02
Hi,

I tried of compiling this prg, as a start to device driver programming. if it gets compiled i thought of inserting it into the kernel using "insmod" and check using "dmesg".

#include <linux/init.h>
#include <linux/module.h>

static int init_module(void)
{
	printk("Init Module\n");
	return (0);
}

static void cleanup_module(void)
{
	printk("Cleanup Module\n");
}

I checked the /usr/src, the kernel headers are there but after giving the full path like

#include </usr/src/linux-headers-2.6.20-15/include/linux/init.h>
#include </usr/src/linux-headers-2.6.20-15/include/linux/module.h>

instead of giving #include <linux/init.h> or <linux/module.h>

I can able to compile the code but with a lot of errors. Does anybody knows any kernel which works fine....

So that i can able to my own kernel and use it for my Device Driver Programing.

Thanks in Advance..

-Rajez-

---

### Post by Zugzwang on 2008-09-02
Please note that it is against the etiquette here to double-post as you did.

With regards to your question: The compiler doesn't find the headers because you didn't tell it where to find it. Only "standard" header files are found automatically (since they are in /usr/include). For the rest, you need to specify the location. Try:

```

gcc -I/usr/src/linux-headers-2.6.20-15/include dd.c

```

Hint: In the future, please *search* for the relevant part of your error message in order to find solutions. You could have easily found [this thread]("http://ubuntuforums.org/showthread.php?t=762412").

---

