---
title: "timer.h : No such file or directory"
date: 2008-04-22
forum: Programming Talk
---

### Post by jsatubnutufroums on 2008-04-22
Hi, 
I write a simple program:
```
#include <stdio.h>
#include <linux/init.h>
#include <linux/timer.h>

int main()
{
        return 0;
}
```
And I compile it by 'gcc -o test test.c' and get the error message:
```
test.c:2:24: error: linux/init.h: No such file or directory
test.c:3:25: error: linux/timer.h: No such file or directory
```
I already install linux-kernel-devel and linux-headers by the following instructions:
```
apt-get install linux-kernel-devel
apt-get install linux-headers-`uname-r'
```
What packages should I install ? How to solve to problem? 
Thank you.

---

### Post by ghostdog74 on 2008-04-22
you can try to find it 
```

find / -type f -name "timer.h"

```

---

### Post by jsatubnutufroums on 2008-04-22
> **ghostdog74 said:**
> you can try to find it 
```

find / -type f -name "timer.h"

```
```
/usr/src/linux-headers-2.6.20-15-server/include/config/scx200hr/timer.h
/usr/src/linux-headers-2.6.20-15-server/include/config/hangcheck/timer.h
/usr/src/linux-headers-2.6.20-15-server/include/config/hpet/timer.h
/usr/src/linux-headers-2.6.20-15-server/include/config/snd/timer.h
/usr/src/linux-headers-2.6.20-15-server/include/config/x86/pm/timer.h
/usr/src/linux-headers-2.6.20-15/include/sound/timer.h
/usr/src/linux-headers-2.6.20-15/include/config/hangcheck/timer.h
/usr/src/linux-headers-2.6.20-15/include/config/hpet/timer.h
/usr/src/linux-headers-2.6.20-15/include/config/x86/cyclone/timer.h
/usr/src/linux-headers-2.6.20-15/include/config/x86/pm/timer.h
/usr/src/linux-headers-2.6.20-15/include/asm-s390/timer.h
/usr/src/linux-headers-2.6.20-15/include/asm-sparc64/timer.h
/usr/src/linux-headers-2.6.20-15/include/asm-sh/cpu-sh2a/timer.h
/usr/src/linux-headers-2.6.20-15/include/asm-sh/cpu-sh2/timer.h
/usr/src/linux-headers-2.6.20-15/include/asm-sh/cpu-sh3/timer.h
/usr/src/linux-headers-2.6.20-15/include/asm-sh/cpu-sh4/timer.h
/usr/src/linux-headers-2.6.20-15/include/asm-sh/timer.h
/usr/src/linux-headers-2.6.20-15/include/asm-sparc/timer.h
/usr/src/linux-headers-2.6.20-15/include/net/irda/timer.h
/usr/src/linux-headers-2.6.20-15/include/asm-i386/timer.h
/usr/src/linux-headers-2.6.20-15/include/linux/sunrpc/timer.h
/usr/src/linux-headers-2.6.20-15/include/linux/timer.h
```
I really find the "timer.h". How could I let the gcc compiler find the "timer.h"? 
Thank you.

---

### Post by jsatubnutufroums on 2008-04-22
```
gcc -o test -I/usr/src/linux-headers-2.6.20-15/include test.c
```
But I get more error messages:
```
In file included from /usr/src/linux-headers-2.6.20-15/include/linux/timer.h:4,
                 from test.c:3:
/usr/src/linux-headers-2.6.20-15/include/linux/list.h:902:2: warning: #warning "don't include kernel headers in userspace"
In file included from /usr/src/linux-headers-2.6.20-15/include/linux/spinlock.h:57,
                 from /usr/src/linux-headers-2.6.20-15/include/linux/timer.h:5,
                 from test.c:3:
/usr/src/linux-headers-2.6.20-15/include/asm/system.h:346: error: expected declaration specifiers or '...' before 'u8'
/usr/src/linux-headers-2.6.20-15/include/asm/system.h:346: error: expected declaration specifiers or '...' before 'u8'
/usr/src/linux-headers-2.6.20-15/include/asm/system.h:347: error: expected declaration specifiers or '...' before 'u16'
/usr/src/linux-headers-2.6.20-15/include/asm/system.h:347: error: expected declaration specifiers or '...' before 'u16'
/usr/src/linux-headers-2.6.20-15/include/asm/system.h:348: error: expected declaration specifiers or '...' before 'u32'
/usr/src/linux-headers-2.6.20-15/include/asm/system.h:348: error: expected declaration specifiers or '...' before 'u32'
/usr/src/linux-headers-2.6.20-15/include/asm/system.h: In function 'cmpxchg_386':
/usr/src/linux-headers-2.6.20-15/include/asm/system.h:355: error: too many arguments to function 'cmpxchg_386_u8'
/usr/src/linux-headers-2.6.20-15/include/asm/system.h:357: error: too many arguments to function 'cmpxchg_386_u16'
/usr/src/linux-headers-2.6.20-15/include/asm/system.h:359: error: too many arguments to function 'cmpxchg_386_u32'
...
```

---

### Post by dwhitney67 on 2008-04-22
Are you trying to build a kernel module?

I built a silly module in which I included "timer.h", and I had no trouble whatsoever.  Here's my sample program and Makefile:

MyKernelModule.c:
[PHP]#include <linux/timer.h>

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
module_exit( goodbye_world );[/PHP]

Makefile:
```
obj-m += MyKernelModule.o
```

To build, I ran this command:
```
make -C /lib/modules/`uname -r`/build M=`pwd`
```

By the way, the kernel headers are located in:
```
/lib/modules/`uname -r`/build/include
```

The path you are using is incorrect.

---

### Post by jsatubnutufroums on 2008-04-22
> **dwhitney67 said:**
> Are you trying to build a kernel module?

I built a silly module in which I included "timer.h", and I had no trouble whatsoever.  Here's my sample program and Makefile:

MyKernelModule.c:
[PHP]#include <linux/timer.h>

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
module_exit( goodbye_world );[/PHP]

Makefile:
```
obj-m += MyKernelModule.o
```

To build, I ran this command:
```
make -C /lib/modules/`uname -r`/build M=`pwd`
```

By the way, the kernel headers are located in:
```
/lib/modules/`uname -r`/build/include
```

The path you are using is incorrect.
How to build a kernel module? Could you teach me ? 
Thank you.

---

### Post by dwhitney67 on 2008-04-22
I do not know what more I can teach you.  I've given you examples of how to create a kernel module and compile it.  Once it is compiled, a kernel-object file is created (e.g. MyKernelModule.ko).

This module can then be loaded using a statement like:
$ sudo insmod MyKernelModule.ko

To unload the module:
$ sudo rmmod MyKernelModule

Note that when unloading the module, the ".ko" extension is not required.

Other than these minimal examples, I have not delved into Linux driver development because I have not had the need to do so.  I'm sure there are tutorials or books concerning the subject, so please Google for them.

---

### Post by jsatubnutufroums on 2008-04-22
Ok~ Thank you.:)

---

### Post by jsatubnutufroums on 2008-04-23
I follow this article ['Kernel/Compile]("http://https://help.ubuntu.com/community/Kernel/Compile")'.
[LIST=1]
[*]sudo apt-get install linux-kernel-devel fakeroot build-essential 
[*]sudo apt-get build-dep linux-source 
[*]apt-get source linux-source 
[*]sudo apt-get install linux-source 
[*]mkdir ~/src 
[*]cd ~/src 
[*]tar xjvf /usr/src/linux-source-<version-number-here>.tar.bz2 
[*]cd linux-source-<version-number-here> 
[*]cp -vi /boot/config-`uname -r` .config 
[*]sudo apt-get install qt3-dev-tools libqt3-mt-dev # if you plan to use 'make xconfig' 
[*]sudo apt-get install libncurses5 # if you plan to use 'make menuconfig' 
[*]make menuconfig 
[*]make-kpkg clean
[*]fakeroot make-kpkg --initrd kernel-image kernel-headers 
[*]sudo dpkg -i linux-image-2.6.20-16-2be-k7_2.6.20-16_i386.deb 
[*]sudo dpkg -i linux-headers-2.6.20-16-2be-k7_2.6.20-16_i386.deb 
[/LIST]
After I reboot the OS, I compile the test.c program and stiil get the same error message. What should I do?:confused:
Thank you.

---

### Post by jsatubnutufroums on 2008-04-23
Comipliation:
```
gcc -o test -I/lib/modules/2.6.20.3-ubuntu1/build/include/ test.c
```
Error Message:
```

In file included from /lib/modules/2.6.20.3-ubuntu1/build/include/linux/timer.h:4,
                 from test.c:1:
/lib/modules/2.6.20.3-ubuntu1/build/include/linux/list.h:902:2: warning: #warning "don't include kernel headers in userspace"
In file included from /lib/modules/2.6.20.3-ubuntu1/build/include/linux/bitops.h:9,
                 from /lib/modules/2.6.20.3-ubuntu1/build/include/linux/thread_info.h:20,
                 from /lib/modules/2.6.20.3-ubuntu1/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.20.3-ubuntu1/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.20.3-ubuntu1/build/include/linux/timer.h:5,
                 from test.c:1:
/lib/modules/2.6.20.3-ubuntu1/build/include/asm/bitops.h:244: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'int'
In file included from /lib/modules/2.6.20.3-ubuntu1/build/include/linux/spinlock.h:57,
                 from /lib/modules/2.6.20.3-ubuntu1/build/include/linux/timer.h:5,
                 from test.c:1:
/lib/modules/2.6.20.3-ubuntu1/build/include/asm/system.h:346: error: expected declaration specifiers or '...' before 'u8'
/lib/modules/2.6.20.3-ubuntu1/build/include/asm/system.h:346: error: expected declaration specifiers or '...' before 'u8'
/lib/modules/2.6.20.3-ubuntu1/build/include/asm/system.h:347: error: expected declaration specifiers or '...' before 'u16'
/lib/modules/2.6.20.3-ubuntu1/build/include/asm/system.h:347: error: expected declaration specifiers or '...' before 'u16'
/lib/modules/2.6.20.3-ubuntu1/build/include/asm/system.h:348: error: expected declaration specifiers or '...' before 'u32'
/lib/modules/2.6.20.3-ubuntu1/build/include/asm/system.h:348: error: expected declaration specifiers or '...' before 'u32'
/lib/modules/2.6.20.3-ubuntu1/build/include/asm/system.h: In function 'cmpxchg_386':
/lib/modules/2.6.20.3-ubuntu1/build/include/asm/system.h:355: error: too many arguments to function 'cmpxchg_386_u8'
/lib/modules/2.6.20.3-ubuntu1/build/include/asm/system.h:357: error: too many arguments to function 'cmpxchg_386_u16'
/lib/modules/2.6.20.3-ubuntu1/build/include/asm/system.h:359: error: too many arguments to function 'cmpxchg_386_u32'
In file included from /lib/modules/2.6.20.3-ubuntu1/build/include/linux/cpumask.h:86,
                 from /lib/modules/2.6.20.3-ubuntu1/build/include/asm/processor.h:22,
                 from /lib/modules/2.6.20.3-ubuntu1/build/include/asm/atomic.h:5,
                 from /lib/modules/2.6.20.3-ubuntu1/build/include/linux/spinlock.h:274,
                 from /lib/modules/2.6.20.3-ubuntu1/build/include/linux/timer.h:5,
                 from test.c:1:
...
...

```

---

### Post by dwhitney67 on 2008-04-23
See this warning message?
```
/lib/modules/2.6.20.3-ubuntu1/build/include/linux/list.h:902:2: warning: #warning "don't include kernel headers in userspace"
```

This is a clue that indicates that you are writing a non-kernel module, yet attempting to include a kernel header file.

All that stuff you did with the apt-gets is not essential, with the exception of:
```
sudo apt-get install linux-kernel-devel
```
and perhaps (which I'm sure you have done previously):
```
sudo apt-get install build-essential
```

Can you please confirm that you are indeed trying to develop a kernel module?  Perhaps it would be better for me (or someone else) to help you if we understood the problem and the solution you seek.

---

### Post by jsatubnutufroums on 2008-04-23
> **dwhitney67 said:**
> See this warning message?
```
/lib/modules/2.6.20.3-ubuntu1/build/include/linux/list.h:902:2: warning: #warning "don't include kernel headers in userspace"
```

This is a clue that indicates that you are writing a non-kernel module, yet attempting to include a kernel header file.

All that stuff you did with the apt-gets is not essential, with the exception of:
```
sudo apt-get install linux-kernel-devel
```
and perhaps (which I'm sure you have done previously):
```
sudo apt-get install build-essential
```

Can you please confirm that you are indeed trying to develop a kernel module?  Perhaps it would be better for me (or someone else) to help you if we understood the problem and the solution you seek.
Yes. I write a non-kernel program. Because I need to call functions which need to include linux/timer.h header. I would like to call a one-shot timer. :)

---

### Post by dwhitney67 on 2008-04-23
Interesting!  Can you tell me more about which kernel service you are attempting to use for this timer?  Is there any documentation (e.g. man-page) for it?

I have code which I wrote long ago for a one-shot timer, along with additional code to support repeating timers, but it does not rely on a kernel service.  Instead it relies on the usage of the C-library select() function.

---

### Post by jsatubnutufroums on 2008-04-23
> **dwhitney67 said:**
> Interesting!  Can you tell me more about which kernel service you are attempting to use for this timer?  Is there any documentation (e.g. man-page) for it?

I have code which I wrote long ago for a one-shot timer, along with additional code to support repeating timers, but it does not rely on a kernel service.  Instead it relies on the usage of the C-library select() function.

I reference [[http://www.xml.com/ldd/chapter/book/ch06.html]](http://www.xml.com/ldd/chapter/book/ch06.html]). 
I develop a client program which communicates with a server. When server sends a 'Download' request to the client, the client has to download a file from File Server at the time that server specifies. So I need a timer to help me do this. I will set the expiration time and the function that executed when time exipred. But I don't know what should I do. So I just google 'linux timer'.

---

### Post by dwhitney67 on 2008-04-24
Below is the link where I store the code I wrote long ago.  The code could probably be done better, and it definitely lacks proper documentation.  Nevertheless, there are some examples demonstrating how to use it.  Perhaps it will serve your needs.  Btw, it is written in C++.

As far as your server and client applications, I trust you can solve those.

[http://www.softhouseproductions.com](http://www.softhouseproductions.com)

---

### Post by jsatubnutufroums on 2008-04-24
Thank you.

---

### Post by rajez79 on 2008-09-03
Itz common that kernel will have errors... first try to solve it. Once the kernel is proper u can start ur device driver programming.

---

