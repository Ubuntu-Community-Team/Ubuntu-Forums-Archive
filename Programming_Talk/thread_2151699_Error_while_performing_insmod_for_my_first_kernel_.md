---
title: "Error while performing insmod for my first kernel programme"
date: 2013-06-05
forum: Programming Talk
---

### Post by Rahul04789 on 2013-06-05
root@rahul-VPCEG28FN:/home/rahul/modules# insmod mod_first.ko 
insmod: error inserting 'mod_first.ko': -1 File exists

---

### Post by dwhitney67 on 2013-06-05
Undoubtedly you have already inserted (loaded) the kernel module in a previous attempt.  Now, when you attempt to load it again, you get the error "File exists".

Try unloading the module before attempting to load it again.
```

$ sudo rmmod mod_first

$ sudo insmod mod_first.ko

```

---

### Post by Rahul04789 on 2013-06-05
Hi all,

Today I started with my first kernel programming and got an error while executing the command "insmod mod_first.ko"
Below is the error message:

[B]root@rahul-VPCEG28FN:/home/rahul/modules# insmod mod_first.ko 
insmod: error inserting 'mod_first.ko': -1 File exists[/B]

**I am also providing my "mod_first.c" file:**

#include<linux/module.h>
#include<linux/init.h>

MODULE_AUTHOR("Rahul");
MODULE_DESCRIPTION("My first kernel module");

int mod_init(void)
{
    printk("\nModule init\n");
    return 0;
}

void mod_exit(void)
{
    printk("\nModule exit\n");
}
module_init(mod_init);
module_exit(mod_exit);

**Following is my makefile:**

obj-m:=mod_first.o

KDIR=/lib/modules/$(shell uname -r)/build

all:
    make -C $(KDIR) M=$(PWD) modules
clean:
    rm -rf *.o *.ko *.mod.*



Please tell me what to be done in oorder to remove the error.
I am very keen/enthusiast to know all these kernel programming.

Regards,

---

### Post by oldos2er on 2013-06-05
Threads merged. Please do not create multiple threads for the same or similar questions.

---

### Post by Rahul04789 on 2013-06-06
Hey thanks! I got it and now working fine..

---

