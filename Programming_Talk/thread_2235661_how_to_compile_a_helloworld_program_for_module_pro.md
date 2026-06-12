---
title: "how to compile a helloworld program for module programming"
date: 2014-07-22
forum: Programming Talk
---

### Post by zerop2 on 2014-07-22
i am using ubuntu 12.04

i search for the error, then find a makefile below

```
all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
```

however after make, return nothing to be done for 'all'

then i change to

```
obj-m += hello.o

hello.o:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```


it result in another error

```
wonder@wonder-VirtualBox:~/layer$ make
cc    -c -o hello.o hello.c
In file included from hello.c:3:0:
/usr/src/linux-headers-3.8.0-29-generic/include/linux/module.h:9:24: fatal error: linux/list.h: No such file or directory
compilation terminated.
make: *** [hello.o] Error 1
```

i use the make file in old version of oreilly book linux device driver

it can make to run, however got error

it use cc, but not gcc, is it modules programming can only use cc, not gcc?

```
make: *** No rule to make target `cli_init.o', needed by `cli.o'.  Stop.
wonder@wonder-VirtualBox:~/layer$ make
cc -D__KERNEL__ -DMODULE -O -Wall -I/usr/src/linux-headers-3.8.0-29-generic/include   -c -o cli.o cli.c
cli.c:1:0: warning: "MODULE" redefined [enabled by default]
<command-line>:0:0: note: this is the location of the previous definition
In file included from /usr/src/linux-headers-3.8.0-29-generic/include/linux/kernel.h:6:0,
                 from /usr/src/linux-headers-3.8.0-29-generic/include/linux/cache.h:4,
                 from /usr/src/linux-headers-3.8.0-29-generic/include/linux/time.h:4,
                 from /usr/src/linux-headers-3.8.0-29-generic/include/linux/stat.h:18,
                 from /usr/src/linux-headers-3.8.0-29-generic/include/linux/module.h:10,
                 from cli.c:2:
/usr/src/linux-headers-3.8.0-29-generic/include/linux/linkage.h:5:25: fatal error: asm/linkage.h: No such file or directory
compilation terminated.
make: *** [cli.o] Error 1
wonder@wonder-VirtualBox:~/layer$ 

```
Makefile:

```
INCLUDEDIR = /usr/src/linux-headers-3.8.0-29-generic/include

CFLAGS = -D__KERNEL__ -DMODULE -O -Wall -I$(INCLUDEDIR)


OBJS = cli.o


all: $(OBJS)

install:
    install -d /lib/modules/$(VER)/misc /lib/modules/misc
    install -c cli.o /lib/modules/$(VER)/misc
    install -c cli.o /lib/modules/misc

clean:
    rm -f *.o *~ core
```

---

### Post by TheFu on 2014-07-22
Not an absolute beginner question - rather should be in the programming forum. Coding a kernel module is NOT a beginner task.

Please use "code tags" when posting code and output.

Looks to me like you need to install the kernel headers.

---

### Post by steeldriver on 2014-07-22
***moved to Programming Talk as suggested by TheFu***

You should really try to find an up-to-date resource - examples from an older book may well not work with the current (3.x) kernels

---

### Post by fugu2 on 2014-07-22
i found this really quickly
```

$ cat hello.c
#include <linux/module.h>
#include <linux/init.h>
MODULE_LICENSE("GPL");
static int __init hello_init(void)
{
  printk("Hello World!\n");
  return 0;
}
static void __exit hello_exit(void)
{
  printk("Unloading hello.\n");
  return;
}
module_init(hello_init);
module_exit(hello_exit);

```
it should work with this Makefile
```

obj-m += hello.o
all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

```
you can test it with
```

$ sudo insmod ./hello.ko 
$ sudo rmmod hello 
$ dmesg | tail

```
FYI, this is not my code
Edit: typo

---

### Post by zerop2 on 2014-07-23
which version of ubuntu do you use ?

i use ubuntu 12 and 14 , have error

---

### Post by zerop2 on 2014-07-23
i succeed to compile , the problem is make, when i type command make, it call cc
but if use the command in makefile, it can run to create ko

are there two make.exe in ubuntu?

why command make that is not call Makefile, 

how to make it run Makefile?

---

### Post by ofnuts on 2014-07-23
A makefile is "executed" by the "make" command, which on Linux is normally the GNU version. If your makefile is not calling the right compiler, or not calling it with the right parameters then the problem is with the makefile, not the make command. 

In Linux there is  "cc" command but it is actually the "gcc" command: 

/usr/bin/cc -> /etc/alternatives/cc -> /usr/bin/gcc

It would also help that you show us the errors that you see...

---

### Post by zerop2 on 2014-07-24
the Makefile is correct and come from googled

what is the problem with make? is console confused and use an another make , which is not for Makefile?

---

### Post by ofnuts on 2014-07-24
> **zerop2 said:**
> the Makefile is correct and come from googled

I have to take your word for it, but since we still don't know what actual error it produces, we cannot tell.

And since you are not able to fix the problem by yourself, you could well be mistaken about this.

---

### Post by CptPicard on 2014-07-24
> **zerop2 said:**
> the Makefile is correct and come from googled

Please don't be "hard to teach". A lot of stuff that comes from Google is not necessarily suitable for your needs as is ;)

I'm sure ofnuts would be of great help if you didn't assume this much. I've been off in Java-land for almost five years now, but I have this distinct feeling that adding CC=gcc to your Makefile might have a pleasant impact on things -- if it does, please seek to understand why.

---

