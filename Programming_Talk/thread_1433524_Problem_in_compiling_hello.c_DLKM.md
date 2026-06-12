---
title: "Problem in compiling hello.c DLKM"
date: 2010-03-19
forum: Programming Talk
---

### Post by vksingh on 2010-03-19
Hi, 

I wrote following DLKM, 

[B]#include <linux/kernel.h>
#include <linux/module.h>
#include <linux/modversions.h>
int init_module()
{
  printk("Hello, world - this is the kernel speaking\n");
  return 0;
}
void cleanup_module()
{
  printk("Short is the life of a kernel module\n");
}


[/B] cc -c hello.c
hello.c:2:27: error: linux/module.h: No such file or directory
hello.c:3:31: error: linux/modversions.h: No such file or directory

I am not able to figure out what is the problem.

Please help.

Thanks,

Vivek

---

### Post by MindSz on 2010-03-19
This might give you a starting point [http://ubuntuforums.org/showthread.php?t=471071](http://ubuntuforums.org/showthread.php?t=471071)

---

### Post by dwhitney67 on 2010-03-19
> **MindSz said:**
> This might give you a starting point [http://ubuntuforums.org/showthread.php?t=471071](http://ubuntuforums.org/showthread.php?t=471071)

In summary, a Makefile like the following is essential:
```

obj-m   := hw.o
hw-objs := hello.o

EXTRA_CFLAGS = -O2

all:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) modules

clean:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) clean
        $(RM) Module.markers modules.order

```

---

