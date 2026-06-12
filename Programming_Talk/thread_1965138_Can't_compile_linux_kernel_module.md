---
title: "Can't compile linux kernel module"
date: 2012-04-25
forum: Programming Talk
---

### Post by misplaced on 2012-04-25
Hi.

I need to compile LKM (Ubuntu 8.04), but compiler have differ opinion:
source:
```
include <kernel.h> 
include <module.h> 

// end of file
```

```

$ gcc -g -D__KERNEL__ -DMODULE -O2 -I/usr/src/linux-headers-2.6.32-122/include -I/usr/src/linux-headers-2.6.32-122-rtai/include -I/usr/src/linux-headers-2.6.32-122/arch/x86/include -o ttt.o ttt.c 
 ... 

 In file included from /usr/src/linux-headers-2.6.32-122/include/linux/prefetch.h:14, 
                  from /usr/src/linux-headers-2.6.32-122/include/linux/list.h:6, 
                  from /usr/src/linux-headers-2.6.32-122/include/linux/module.h:9, 
                  from ttt.c:5: 
 /usr/src/linux-headers-2.6.32-122/arch/x86/include/asm/processor.h:116: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function) 
 /usr/src/linux-headers-2.6.32-122/arch/x86/include/asm/processor.h:116: error: requested alignment is not a constant 

 ... 

 /usr/src/linux-headers-2.6.32-122/arch/x86/include/asm/processor.h: In function ‘load_cr3’: 
 /usr/src/linux-headers-2.6.32-122/arch/x86/include/asm/processor.h:193: error: ‘CONFIG_PAGE_OFFSETUL’ undeclared (first use in this function) 
 /usr/src/linux-headers-2.6.32-122/arch/x86/include/asm/processor.h:193: error: (Each undeclared identifier is reported only once 
 /usr/src/linux-headers-2.6.32-122/arch/x86/include/asm/processor.h:193: error: for each function it appears in.) 
 /usr/src/linux-headers-2.6.32-122/arch/x86/include/asm/processor.h: At top level: 
 /usr/src/linux-headers-2.6.32-122/arch/x86/include/asm/processor.h:242: error: requested alignment is not a constant 
 /usr/src/linux-headers-2.6.32-122/arch/x86/include/asm/processor.h:273: error: requested alignment is not a constant
...

```
What is CONFIG_X86_L1_CACHE_SHIFT and where it defined?

I read many examples of "Hello world" LKM. All of it begins with #include <linux/kernel.h> and <linux/module.h>. What i'm does wrong?

---

### Post by dwhitney67 on 2012-04-25
Try using a Makefile to build a kernel module, not gcc.

This example Makefile _may_ work for your needs:
```

obj-m := ttt.o

KDIR  := /lib/modules/$(shell uname -r)/build

all:
        $(MAKE) -C $(KDIR) M=$(PWD) modules

clean:
        $(MAKE) -C $(KDIR) M=$(PWD) clean

```
Note that the Makefile above uses the system's running kernel version.  If that differs from the version that you are targeting, then adjust the shell statement above.

---

