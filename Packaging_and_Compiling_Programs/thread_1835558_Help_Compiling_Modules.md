---
title: "Help Compiling Modules"
date: 2011-08-29
forum: Packaging and Compiling Programs
---

### Post by emiller12345 on 2011-08-29
Having trouble when compiling modules && trying to make use of certain includes like stdio.h and stdlib.h.  Does anyone have an explanation || solution?

```
#include <stdlib.h>
#include <linux/init.h>
#include <linux/module.h>

static int test_init(void)
{
    printk(KERN_INFO "Hello\n");
    char szNumbers[] = "2001 60c0c0 -1101110100110100100000 0x6fffff";
    char * pEnd;
    long int li1, li2, li3, li4;
    li1 = strtol (szNumbers,&pEnd,10);
    li2 = strtol (pEnd,&pEnd,16);
    li3 = strtol (pEnd,&pEnd,2);
    li4 = strtol (pEnd,NULL,0);
    printk(KERN_INFO "The decimal equivalents are: %ld, %ld, %ld and %ld.\n", li1, li2, li3, li4);
    return 0;
}


static void test_exit(void)
{
    printk(KERN_INFO "Goodbye\n");
}


module_init(test_init);
module_exit(test_exit);

MODULE_LICENSE("GPL");
MODULE_AUTHOR("emiller12345");    
MODULE_DESCRIPTION("a test lkm");
MODULE_SUPPORTED_DEVICE("test");

```

---

### Post by emiller12345 on 2011-08-29
The Makefile I'm using is 
```

obj-m += test.o

all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

```

---

### Post by SevenMachines on 2011-08-30
You cant use the c library in kernel modules, you need to drop the stdlib.h include and use simple_strtol (i think) from the kernel api instead of strtol

---

### Post by SevenMachines on 2011-08-30
See [http://www.kernel.org/doc/htmldocs/kernel-api/libc.html](http://www.kernel.org/doc/htmldocs/kernel-api/libc.html)

---

### Post by emiller12345 on 2011-08-31
Ah, Thank you for the reference.  I figured there was something different in making lkm's.  I'm not sure why but simply substituting in the new command allows me to compile and execute, but it doesn't behave the exactly the same. The first entry of the string is recognized, but the rest are read as zero.

```

kernel: [ 6859.777414] Hello
kernel: [ 6859.777416] The decimal equivalents are: 2001, 0, 0 and 0.
kernel: [ 6859.789342] Goodbye

```

I think the values should be about 2001, 6340800, -216352, and 7340031
Any good ideas why this is? Something tells me pEnd is not being used properly here.

---

### Post by SevenMachines on 2011-09-01
My guess would be that the 'simple' in simple_strtol means 'no whitespace trimming' but I couldnt say for sure until I look it up somewhere, or someone who knows these things can fill us in? :)

[EDIT] Seems to be the case, trimming the whitespace manually will give you the right results

---

