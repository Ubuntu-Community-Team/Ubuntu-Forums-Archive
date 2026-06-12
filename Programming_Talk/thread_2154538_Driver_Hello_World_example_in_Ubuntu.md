---
title: "Driver Hello World example in Ubuntu"
date: 2013-06-15
forum: Programming Talk
---

### Post by johanngomes on 2013-06-15
Hi, i have in the same folder the following archives:

hello.c

```
#include <linux/init.h>#include <linux/module.h>


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
```

Makefile

```

obj-m += hello.o
all:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

```

When i run the command ```
make
``` in the folder where there is this archives, i get:

```
make -C /lib/modules/3.5.0-34-generic/build M=/home/johann/Desktop/8º Período/Infra-Estrutura de Software/driver-linux modulesmake[1]: Entering directory `/usr/src/linux-headers-3.5.0-34-generic'
make[1]: *** No rule to make target `Período/Infra-Estrutura'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-34-generic'
make: *** [all] Error 2



```

What am i missing? Thanks in advance :p

---

### Post by Bucky Ball on 2013-06-15
*Thread moved to **Programming Talk**.*

---

### Post by xb12x on 2013-06-15
> **johanngomes said:**
> Hi, i have in the same folder the following archives:

hello.c

```

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
```

Makefile

```

obj-m += hello.o
all:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

```

When i run the command ```
make
``` in the folder where there is this archives, i get:

```

make -C /lib/modules/3.5.0-34-generic/build M=/home/johann/Desktop/8º Período/Infra-Estrutura de Software/driver-linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-34-generic'
make[1]: *** No rule to make target `Período/Infra-Estrutura'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-34-generic'
make: *** [all] Error 2

```

What am i missing? Thanks in advance :p


The folder's path contains spaces. Create a folder with no spaces in the path: 
/home/johann/drivers/hello

---

### Post by dwhitney67 on 2013-06-16
> **johanngomes said:**
> 
What am i missing? Thanks in advance :p

It's not what your missing, but what you have.  You have white-space in your directory names, and that is confusing the 'make' command.  Simply surrounding the $(PWD) with double-quotes will not solve the problem.  Thus unless someone else chimes in with a brilliant suggestion, my suggestion right now is for you to rename your directories to eliminate the white-space.

For example:
```

/home/johann/Desktop/**8ºPeríodo**/**Infra-EstruturaDeSoftware**/driver-linux

```

---

### Post by zobayer1 on 2013-06-17
> **johanngomes said:**
> Hi, i have in the same folder the following archives:

hello.c

```
#include <linux/init.h>#include <linux/module.h>


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
```

Makefile

```

obj-m += hello.o
all:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

```

When i run the command ```
make
``` in the folder where there is this archives, i get:

```
make -C /lib/modules/3.5.0-34-generic/build M=/home/johann/Desktop/8º Período/Infra-Estrutura de Software/driver-linux modulesmake[1]: Entering directory `/usr/src/linux-headers-3.5.0-34-generic'
make[1]: *** No rule to make target `Período/Infra-Estrutura'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-34-generic'
make: *** [all] Error 2



```

What am i missing? Thanks in advance :p

I have written a similar thing few years back, and faced same sort of problems, I fixed it by not using any space in the directory names and instead of $(PWD) I had to use $(shell pwd), I still have no idea why $(PWD) did not work...

Here is the example [http://zobayer.blogspot.com/2011/07/simple-character-device.html ]("http://zobayer.blogspot.com/2011/07/simple-character-device.html")

---

