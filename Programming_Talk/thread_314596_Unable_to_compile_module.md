---
title: "Unable to compile module"
date: 2006-12-07
forum: Programming Talk
---

### Post by vze4p6c2 on 2006-12-07
Hey fellas,

I have been trying to compile and run a simple module from "Linux Device Drivers", and have been unsuccessful lately.  I'm a nooby at this point, so I've also looked through simple module codes and they seem to be the same comparing to the one in the book.  I use C language.  Here the code to be compiled:

```

#define MODULE
#include <linux/module.h>

int init_module(void) {
        printk("<1>The module has started...\n");
        return 0;
}

void cleanup_module(void) {
        printk("<1>The module has ended...\n");
}

```

I used a GCC compiler to compile the code:

```

gcc -c code.c

```

But I get the following reply from the compiler:

```

In file included from /usr/include/linux/sched.h:16,
                 from /usr/include/linux/module.h:9,
                 from code.c:2:
/usr/include/linux/signal.h:2:2: warning: #warning "You should include <signal.h>. This time I will do it for you."
In file included from /usr/include/linux/resource.h:4,
                 from /usr/include/linux/sched.h:79,
                 from /usr/include/linux/module.h:9,
                 from code.c:2:
/usr/include/linux/time.h:9: error: redefinition of &#8216;struct timespec&#8217;
/usr/include/linux/time.h:15: error: redefinition of &#8216;struct timeval&#8217;
/usr/include/linux/time.h:20: error: redefinition of &#8216;struct timezone&#8217;
/usr/include/linux/time.h:47: error: redefinition of &#8216;struct itimerval&#8217;
In file included from code.c:2:
/usr/include/linux/module.h:41: error: field &#8216;attr&#8217; has incomplete type
/usr/include/linux/module.h:49: error: field &#8216;kobj&#8217; has incomplete type


```

If you guys are good at device drivers, some help resolving this issue would be really apperciated.

Thanks,
Vlad

---

### Post by yogi9119 on 2009-10-29
Hi,

Even i'm facing same problem in this simple hello world program. 
let me tell you what all the things i tried
1) When i went to compile simple hello world program, i was getting the error,

#define MODULE
#include <linux/module.h>
int init_module(void) { printk("<1>Hello, world\n"); return 0; }
void cleanup_module(void) { printk("<1>Goodbye cruel world\n"); }

linux/module.h missing.. 

2) when i googled it, i came to know i need to compile my kernel and do the same.
3) i downloaded the kernel and i was able to compile the kernel, by following the steps given in HOWTO compile kernel.

4) I also installed the compiled kernel in my machine.
5) Now when i tried to compile the same code again. It gives me the same error.
6) Again i googled and found few things like creating a make file etc.

Makefile looks like this
[COLOR=#000000]obj-m += hello-1.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean[/COLOR] 

I also tried many other combinations of it.  like

gcc -DMODULE -D__KERNEL__  -c hello.c 
etc...


But still nothing is working.

7) I'm not able to compile the code. Please help me.:(

Rgds

---

### Post by Zugzwang on 2009-10-29
> **yogi9119 said:**
> 
7) I'm not able to compile the code. Please help me.:(


You need to tell the compiler where (i.e., in which path) to find the include files (in my case, /usr/src/linux-headers-2.6.28-14). There are plenty of examples on how to do this on this board. Use the search function to find them.

---

### Post by dwhitney67 on 2009-10-29
> **yogi9119 said:**
> Hi,

Even i'm facing same problem in this simple hello world program. 
let me tell you what all the things i tried
1) When i went to compile simple hello world program, i was getting the error,

#define MODULE
#include <linux/module.h>
int init_module(void) { printk("<1>Hello, world\n"); return 0; }
void cleanup_module(void) { printk("<1>Goodbye cruel world\n"); }

linux/module.h missing.. 

2) when i googled it, i came to know i need to compile my kernel and do the same.
3) i downloaded the kernel and i was able to compile the kernel, by following the steps given in HOWTO compile kernel.

4) I also installed the compiled kernel in my machine.
5) Now when i tried to compile the same code again. It gives me the same error.
6) Again i googled and found few things like creating a make file etc.

Makefile looks like this
[COLOR=#000000]obj-m += hello-1.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean[/COLOR] 

I also tried many other combinations of it.  like

gcc -DMODULE -D__KERNEL__  -c hello.c 
etc...


But still nothing is working.

7) I'm not able to compile the code. Please help me.:(

Rgds

Your Makefile, if it is syntactically correct, should have worked.  Since you failed to place your code within CODE tags, I have no idea if the syntax is correct.  Your Makefile should look something like, where <tab> is an actual tab-space:
```

obj-m += hello-1.o

all:
<tab>make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
<tab>make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean 

```
With respect to your code (hello-1.c), it should look something like:
```

#include <linux/module.h>      // Needed by all modules

#define DRIVER_AUTHOR "FirstName LastName <email@addr.com>"
#define DRIVER_DESC   "A Hello World kernel module."

MODULE_LICENSE("GPL");
MODULE_AUTHOR(DRIVER_AUTHOR);            /* Who wrote this module? */
MODULE_DESCRIPTION(DRIVER_DESC);         /* What does this module do */


static int __init hello_world( void )
{
  printk("<1>Hello, world\n");
  return 0;
}

static void __exit goodbye_world( void )
{
  printk("<1>Goodbye cruel world\n");
}

module_init( hello_world );
module_exit( goodbye_world );

```

---

### Post by dwhitney67 on 2009-10-29
> **Zugzwang said:**
> You need to tell the compiler where (i.e., in which path) to find the include files (in my case, /usr/src/linux-headers-2.6.28-14). There are plenty of examples on how to do this on this board. Use the search function to find them.

The portable way to indicate where the Linux source code is located is to specify /lib/modules/`uname -r`/build.

Not all Linux systems place the source in /usr/src.

---

### Post by Zugzwang on 2009-10-29
> **dwhitney67 said:**
> The portable way to indicate where the Linux source code is located is to specify /lib/modules/`uname -r`/build.

Not all Linux systems place the source in /usr/src.

Interesting. I would not have excepted such data in the "lib" section of the file system. Thanks for the clarification.

---

