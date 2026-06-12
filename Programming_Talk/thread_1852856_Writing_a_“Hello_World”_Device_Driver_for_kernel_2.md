---
title: "Writing a “Hello World” Device Driver for kernel 2.6 using Eclipse"
date: 2011-10-01
forum: Programming Talk
---

### Post by isaacarsenal on 2011-10-01
[SIZE=3]**Goal**[/SIZE]

I am trying to write a simple device driver on Ubuntu. I want to do this  using Eclipse (that I found it a good IDE for driver  programming). Here is the code:

```

#include <linux/module.h>

static int __init hello_world( void )
{
  printk( "hello world!\n" );
  return 0;
}

static void __exit goodbye_world( void )
{
  printk( "goodbye world!\n" );
}

module_init( hello_world );
module_exit( goodbye_world );
```[B][SIZE=3]
My Effort[/SIZE][/B]
After some research, I decided to use [Eclipse CTD]("http://www.eclipse.org/cdt/") for developing the driver (while I am still not sure if it supports multi-threading debugging tools). So I have:


[LIST=1]
[*]Installed [Ubuntu 11.04 desktop x86]("http://www.ubuntu.com/start-download?distro=desktop&bits=32&release=latest") on a VMWare virtual machine,
[*]Installed eclipse-cdt and [linux-headers-2.6.38-8]("http://packages.ubuntu.com/linux-headers-2.6.38-8") using Synaptic Package Manager,
[*]Created a C Project named TestDriver1 and copy-pasted above code to it,
[*]Changed the default build command, make, to the following customized build command:
[/LIST]
```
make -C /lib/modules/2.6.38-8-generic/build M=/home/isaac/workspace/TestDriver1
```**[SIZE=3]The Problem[/SIZE]**
I get an error when I try to build this project using eclipse. Here is the log for the build:
```

**** Build of configuration Debug for project TestDriver1 ****

make -C /lib/modules/2.6.38-8-generic/build M=/home/isaac/workspace/TestDriver1 all

make: Entering directory '/usr/src/linux-headers-2.6.38-8-generic'

make: *** No rule to make target vmlinux', needed byall'. Stop.

make: Leaving directory '/usr/src/linux-headers-2.6.38-8-generic'
```Interestingly, I get no error when I use **shell** instead of **eclipse** to build this project. For shell, I just create a **Makefile** containing ```
obj-m += TestDriver1.o
``` and use the above **make** command to build.

So, something must be wrong with the eclipse **Makefile**. Maybe it is looking for the **vmlinux** architecture (?) or something while current architecture is **x86**. Maybe it's because of VMWare?

As I understood, eclipse creates the makefiles automatically and modifying it manually would cause errors in the future OR make managing makefile difficult.

So, how can I compile this project on eclipse?

---

