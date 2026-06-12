---
title: "module.h"
date: 2007-10-24
forum: Programming Talk
---

### Post by podiyan on 2007-10-24
I was trying to compile this program

#define MODULE
#include <linux/module.h>

int init_module (void) /* Loads a module in the kernel */
{
printk("Hello kernel n");
return 0;
}

void cleanup_module(void) /* Removes module from kernel */
{
printk("GoodBye Kerneln");
}

but in ubuntu i cant find module.h


Thanks in advance 

Please help me.

---

### Post by podiyan on 2007-10-24
please tell me where is file module.h 
i searched in /usr/include/linux/
but there was no file.

Please help me

---

### Post by moma on 2007-10-24
Hello,

Take a look at this example module.  It uses a Makefile.
[http://ubuntuforums.org/showthread.php?p=3486457#post3486457](http://ubuntuforums.org/showthread.php?p=3486457#post3486457)
Read also what the prerequisites to compile a module are.


Kernel knowledge: [http://www.futuredesktop.net/kernel.html](http://www.futuredesktop.net/kernel.html)

---

### Post by gradedcheese on 2007-10-24
That's not enough code for a Linux kernel module... please read this instead: [http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/) (one of the first chapters explains what you're trying to do)

---

