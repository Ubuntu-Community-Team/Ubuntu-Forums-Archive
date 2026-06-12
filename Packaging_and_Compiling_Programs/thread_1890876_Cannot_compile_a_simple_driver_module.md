---
title: "Cannot compile a simple driver module"
date: 2011-12-04
forum: Packaging and Compiling Programs
---

### Post by Pouyaaa on 2011-12-04
I'm newbie at driver module programming.... I've written a very simple hello world module then I wanna compile it , I got this result :
```

make -C /lib/modules/2.6.38-8-generic/build M=/root/ker modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [all] Error 2

```

Also I've installed linux headers via following command 
```
apt-get install linux-headers-2.6.38-8-generic
```

here is my Makefile file
```

obj-m += hello.o

all:
        make -C /lib/modules/$(shell uname -r)/build M=$(shell pwd) modules

clean:
        make -C /lib/modules/$(shell uname -r)/build M=$(shell pwd) clean

```

Also I gotta note that , the "build" is not exist at that folder:)

my source code :

```

#include <linux/module.h>
#include <linux/kernel.h>
 
int init_module(void)
{
        printk(KERN_INFO "init_module() called\n");
        return 0;
}
 
void cleanup_module(void)
{
        printk(KERN_INFO "cleanup_module() called\n");
}

```


[LIST]
[*]thanks
[/LIST]

---

