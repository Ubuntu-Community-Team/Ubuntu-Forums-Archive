---
title: "kernel module error"
date: 2010-10-07
forum: Programming Talk
---

### Post by thelast on 2010-10-07
hello,

I am trying to write kernel module, when I compile the code, I facing this error

```

make: Entering directory `/usr/src/linux-headers-2.6.24-24-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[1]: *** No rule to make target `arch/x86/kernel/asm-offsets.c', needed by `arch/x86/kernel/asm-offsets.s'.  Stop.
make: *** [prepare0] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.24-24-generic'

```

where is the problem?

thanks

---

### Post by dwhitney67 on 2010-10-07
Is your intent to rebuild the entire kernel, or just a single module?  The output you posted seems to imply the former.

If you can, please post the Makefile you are using.


P.S.  Building the entire kernel is possible, but of course you must have the kernel source (.h and .c) files.  With Ubuntu, typically all you have are the kernel header (.h) files, unless you go out of your way to get the kernel source files.

---

### Post by thelast on 2010-10-08
thanks for your replay.

No, I want to build just a single module.
the code as below:

```
#include <linux/kernel.h>
#include <linux/module.h>
#include <linux/moduleparam.h>
#include <linux/unistd.h>
#include <asm/semaphore.h>
#include <asm/cacheflush.h>

void **sys_call_table;

asmlinkage int (*original_call) (const char*, int, int);

asmlinkage int our_sys_open(const char* file, int flags, int mode)
{
   printk("A file was opened\n");
   return original_call(file, flags, mode);
}

int set_page_rw(long unsigned int _addr)
{
   struct page *pg;
   pgprot_t prot;
   pg = virt_to_page(_addr);
   prot.pgprot = VM_READ | VM_WRITE;
   return change_page_attr(pg, 1, prot);
}

int init_module()
{
    sys_call_table = (void*)0xc061e4e0;
    original_call = sys_call_table[__NR_open];

    set_page_rw(sys_call_table);
    sys_call_table[__NR_open] = our_sys_open;
}

void cleanup_module()
{
   // Restore the original call
   sys_call_table[__NR_open] = original_call;
}


```

and makefile is:

```
obj?m += hook_open?1.o


```
notes:
1- the code not for malicious purpose, it's just for student's research project. 
2- I am working on Ubuntu 8.04.

thanks a lot

---

### Post by dwhitney67 on 2010-10-08
Your Makefile should look something like:
```

obj-m := hook_open.o

all:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) modules

clean:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) clean
        $(RM) Module.markers modules.order

```
This Makefile and your source file should be placed together in a folder, perhaps relative to your home directory.

To build the kernel module, just run "make".

The module you posted will generate compiler errors, which of course must be corrected before the kernel object module is created.

Once you have created the kernel object module, you can insert it into the kernel using the following:
```

sudo insmod hook_open.ko

```
To remove it from the kernel:
```

sudo rmmod hook_open

```

P.S.  You do *not* need to have 'sudo' privileges to build the kernel module.

---

### Post by thelast on 2010-10-09
Thank you for your reply.

Well I am now I have a folder on a file containing the open_hook.c
In addition to the file makefile As follows:


```
obj-m := hook_open.o

all:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) modules

clean:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) clean
        $(RM) Module.markers modules.order
```

but when I execute it I get an error:

```
:~/module/Open$ make
make: Nothing to be done for `all'
```

 why?

---

### Post by thelast on 2010-10-09
> **dwhitney67 said:**
> 

Once you have created the kernel object module, you can insert it into the kernel using the following:
```

sudo insmod hook_open.ko

```
To remove it from the kernel:
```

sudo rmmod hook_open

```


I know that , [from here]("http://ubuntuforums.org/showpost.php?p=4998144&postcount=2"), thanks.
but why the error now appear?

can you compile my module on your PC, and tell me the result?

by the way, HelloWorld's module executed correctly on my PC.

---

### Post by dwhitney67 on 2010-10-09
> **thelast said:**
> ...
but when I execute it I get an error:

```
:~/module/Open$ make
make: Nothing to be done for `all'
```

 why?

Make sure you have the development tools installed on your system:
```

sudo apt-get install build-essential

```
And obviously the kernel header files:
```

sudo apt-get install linux-headers-`uname -r`

```

---

