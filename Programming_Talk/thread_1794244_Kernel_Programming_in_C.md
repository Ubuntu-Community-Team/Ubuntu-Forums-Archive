---
title: "Kernel Programming in C"
date: 2011-06-30
forum: Programming Talk
---

### Post by zobayer1 on 2011-06-30
I am trying to learn karnel programming for my system programming lab @ university. So, I just tried the first sample hello-1.c
```

#include <linux/module.h>
#include <linux/kernel.h>

int init_module(void) {
    printk(KERN_INFO "Hello world 1.\n");
    return 0;
}

void cleanup_module(void) {
    printk(KERN_INFO "Goodbye cruel world 1.\n");
}

```

To compile this file, I've written the following Makefile
```

obj-m += hello-1.o

all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

```

When I try to run this file using make command (obviously using sudo) I get following error:
```

zobayer@zobayer:~/Lab/system/kernel$ sudo make
[sudo] password for zobayer: 
make -C /lib/modules/2.6.38-8-generic/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf --silentoldconfig Kconfig
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  UPD     include/generated/utsrelease.h
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [all] Error 2
zobayer@zobayer:~/Lab/system/kernel$

```

Can anyone please tell me what's wrong here?

---

### Post by megabytemonster on 2011-07-01
In your makefile you have:

```
make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
```

But then when you run it, it's displayed as:

```
make -C /lib/modules/2.6.38-8-generic/build M= modules
```

As you can see there's nothing after the M=, so $(PWD) is failing to print out your working directory.

---

### Post by emiller12345 on 2011-07-01
try a lowercase PWD like this
```
make -C /lib/modules/$(shell uname -r)/build M=$(pwd) modules
```

---

### Post by zobayer1 on 2011-07-01
> **megabytemonster said:**
> In your makefile you have:

```
make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
```But then when you run it, it's displayed as:

```
make -C /lib/modules/2.6.38-8-generic/build M= modules
```As you can see there's nothing after the M=, so $(PWD) is failing to print out your working directory.

Yes, but I don't know why, when I use it in terminal it prints working directory.

> **emiller12345 said:**
> try a lowercase PWD like this
```
make -C /lib/modules/$(shell uname -r)/build M=$(pwd) modules
```

As I expected, the problem is not there. Can you suggest me anything more?

---

### Post by zobayer1 on 2011-07-01
Finally I got it, I changed this and it worked:
```

make -C /lib/modules/$(shell uname -r)/build M=$(pwd) modules

```to

```

make -C /lib/modules/$(shell uname -r)/build M=$(shell pwd) modules

```I had the desired output:
```

zobayer@zobayer:~/Lab/system/kernel$ sudo make
make -C /lib/modules/2.6.38-8-generic/build M=/home/zobayer/Lab/system/kernel modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
zobayer@zobayer:~/Lab/system/kernel$

```Thanks **megabytemonster **and** emiller12345 **for your help.

---

### Post by emiller12345 on 2011-07-01
no problem

---

### Post by ankur.rastogi on 2011-08-26
Hi,

I did the same, and it worked with Ubuntu 10.4 LTS Desktop Edition.

Regards.

Ankur

---

### Post by ktnamus on 2012-12-05
i  tried all these ***three possibilities***
 but on my ubuntu 12.04LTS linux **3.2.0-23-generic.**
**not working**. try to solve my problem. i have wasted three hours to reading & trying these
**** posts

---

### Post by CharlesA on 2012-12-05
Thread closed as it is over a year old. Please create a new thread detailing your problems and *please* watch your language.

---

