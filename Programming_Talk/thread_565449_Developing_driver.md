---
title: "Developing driver"
date: 2007-10-02
forum: Programming Talk
---

### Post by resistantgnome on 2007-10-02
I tried my first driver code. Book said the code will compile and run under linux kernel version 2.0 to 2.4. I don't have an older kernel. I am using Ubuntu 7.04(Kernel 2.6.20-16-generic). 
When I do this 
```
gcc -c test.c
```
Code gives an error
```
test.c:2:26: error: linux/module.h: No such file or directory
```
```

#define MODULE
#include <linux/module.h>
 
int init_module(void)
{
     printk("<1>Hello, world\n");
     return 0;
}
void cleanup_module(void)
{
     printk("<1>Goodbye cruel world\n");
}


```

Is there any way I can make this code work?

---

### Post by immortal_cro on 2007-10-02
Try using this Makefile:
```

obj-m += drajver.o

all:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

```

---

### Post by resistantgnome on 2007-10-02
What does it do?
I should just do **make** in the directory in which I have this code?

---

