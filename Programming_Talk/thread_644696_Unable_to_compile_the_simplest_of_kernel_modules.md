---
title: "Unable to compile the simplest of kernel modules"
date: 2007-12-19
forum: Programming Talk
---

### Post by thejdev on 2007-12-19
I'm running x86_64 gutsy on an AMD 64 bit dual core machine (1 GB RAM,200 GB SATA HDD)  but I dont have an internet connection . I've installed the build-essential packages for gcc,g++ and libc6-dev that come along with the live cd and have installed the kernel headers package for kernel 2.6.22-14 that comes as a .deb package on the ubuntu website . 
      I tried to compile a simple hello world kernel module (see below) :

[PHP]//hello.c in root folder

#include <linux/kernel.h>
#include <linux/module.h>

#if CONFIG_MODVERSIONS == 1
#define MODVERSIONS
#include <linux/modversions.h>
#endif

int init_module()
{
     printk("\n\nHello world \n\n");
     return(0);
}

void cleanup_module()
{printk("\n\nBye\n\n");}


root@Babu:/# gcc -I /usr/src/linux-headers-2.6.22-14/include -Wall -D__KERNEL__ -DMODULE -c hello.c
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/kernel.h:11,
                 from hello.c:1:
/usr/src/linux-headers-2.6.22-14/include/linux/linkage.h:4:25: error: asm/linkage.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/kernel.h:15,
                 from hello.c:1:
/usr/src/linux-headers-2.6.22-14/include/linux/bitops.h:9:24: error: asm/bitops.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/kernel.h:15,
                 from hello.c:1:
/usr/src/linux-headers-2.6.22-14/include/linux/bitops.h: In function ‘get_bitmask_order’:
/usr/src/linux-headers-2.6.22-14/include/linux/bitops.h:15: warning: implicit declaration of function ‘fls’
/usr/src/linux-headers-2.6.22-14/include/linux/bitops.h: In function ‘hweight_long’:
/usr/src/linux-headers-2.6.22-14/include/linux/bitops.h:31: warning: implicit declaration of function ‘hweight32’
/usr/src/linux-headers-2.6.22-14/include/linux/bitops.h:31: warning: implicit declaration of function ‘hweight64’
/usr/src/linux-headers-2.6.22-14/include/linux/bitops.h: In function ‘fls_long’:
/usr/src/linux-headers-2.6.22-14/include/linux/bitops.h:58: warning: implicit declaration of function ‘fls64’
In file included from hello.c:1:
/usr/src/linux-headers-2.6.22-14/include/linux/kernel.h:18:21: error: asm/bug.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/preempt.h:9,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:49,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 from hello.c:2:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:21:29: error: asm/thread_info.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/preempt.h:9,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:49,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 from hello.c:2:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h: At top level:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:30: warning: ‘struct thread_info’ declared inside parameter list
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:30: warning: its scope is only this definition or declaration, which is probably not what you want
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h: In function ‘set_ti_thread_flag’:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:32: warning: implicit declaration of function ‘set_bit’
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:32: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h: At top level:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:35: warning: ‘struct thread_info’ declared inside parameter list
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h: In function ‘clear_ti_thread_flag’:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:37: warning: implicit declaration of function ‘clear_bit’
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:37: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h: At top level:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:40: warning: ‘struct thread_info’ declared inside parameter list
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h: In function ‘test_and_set_ti_thread_flag’:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:42: warning: implicit declaration of function ‘test_and_set_bit’
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:42: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h: At top level:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:45: warning: ‘struct thread_info’ declared inside parameter list
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h: In function ‘test_and_clear_ti_thread_flag’:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:47: warning: implicit declaration of function ‘test_and_clear_bit’
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:47: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h: At top level:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:50: warning: ‘struct thread_info’ declared inside parameter list
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h: In function ‘test_ti_thread_flag’:
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:52: warning: implicit declaration of function ‘test_bit’
/usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:52: error: dereferencing pointer to incomplete type
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 from hello.c:2:
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:57:24: error: asm/system.h: No such file or directory
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:326:24: error: asm/atomic.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,
                 from hello.c:2:
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h: At top level:
/usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:332: error: expected ‘)’ before ‘*’ token
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/list.h:8,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:10,
                 from hello.c:2:
/usr/src/linux-headers-2.6.22-14/include/linux/prefetch.h:14:27: error: asm/processor.h: No such file or directory
/usr/src/linux-headers-2.6.22-14/include/linux/prefetch.h:15:23: error: asm/cache.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:10,
                 from hello.c:2:
/usr/src/linux-headers-2.6.22-14/include/linux/list.h: In function ‘__list_add_rcu’:
/usr/src/linux-headers-2.6.22-14/include/linux/list.h:100: warning: implicit declaration of function ‘smp_wmb’
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/time.h:7,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/stat.h:60,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:11,
                 from hello.c:2:
/usr/src/linux-headers-2.6.22-14/include/linux/seqlock.h: In function ‘read_seqbegin’:
/usr/src/linux-headers-2.6.22-14/include/linux/seqlock.h:89: warning: implicit declaration of function ‘smp_rmb’
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/kobject.h:25,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:17,
                 from hello.c:2:
/usr/src/linux-headers-2.6.22-14/include/linux/kref.h: At top level:
/usr/src/linux-headers-2.6.22-14/include/linux/kref.h:24: error: expected specifier-qualifier-list before ‘atomic_t’
In file included from /usr/src/linux-headers-2.6.22-14/include/linux/kobject.h:27,
                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:17,
                 from hello.c:2:
/usr/src/linux-headers-2.6.22-14/include/linux/wait.h:26:25: error: asm/current.h: No such file or directory
In file included from hello.c:2:
/usr/src/linux-headers-2.6.22-14/include/linux/module.h:19:23: error: asm/local.h: No such file or directory
/usr/src/linux-headers-2.6.22-14/include/linux/module.h:21:24: error: asm/module.h: No such file or directory[/PHP]

Whoa someone's unhappy !

I'm not allowed an internet connection on my comp as I live in a hostel , so could someone please direct me how to get the build essential package for kernel headers through windows . I've been trying for over a week now , unsuccessfully

---

### Post by moma on 2007-12-19
Hello,

Take a look at this module example.
[http://ubuntuforums.org/showthread.php?p=3486457#post3486457](http://ubuntuforums.org/showthread.php?p=3486457#post3486457)

Note that "/lib/modules/$(uname -r)/build" is normally a symbolic link to /usr/src/linux-headers....

$ [COLOR="SeaGreen"]ls -l /lib/modules/$(uname -r)/build[/COLOR]
lrwxrwxrwx 1 root root 40 2007-10-10 10:47 /lib/modules/2.6.22-14-generic/build -> /usr/src/linux-headers-2.6.22-14-generic

Study also the guides under "Driver and module programming" of [this guide.]("http://www.futuredesktop.net/kernel.html")
---- ---- ---- ---- ---- ---- ---- ---- 

Downloading packages for your offline system.

As you already know, you will need at least these components. (The examples are taken from my 32 bits Ubuntu) 
$ [COLOR="SeaGreen"]apt-cache search  linux-headers-$(uname -r)[/COLOR]
linux-headers-2.6.22-14-generic - Linux kernel headers for version 2.6.22 on x86/x86_64

$ [COLOR="SeaGreen"]apt-cache search build-essential[/COLOR]
build-essential - informational list of build-essential packages
---

Browse to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and search for the package names.

Download the (.deb) packages for your system (is it a 64-bits Gutsy?)
Important: Take also all depending packages ! Eg. the "build-essential" pack has [these dependencies.... ]("http://packages.ubuntu.com/gutsy/devel/build-essential"), Ok?

Use the "dpkg -i" command to install the packages on your offline system.
$[COLOR="SeaGreen"] sudo dpkg -i *deb [/COLOR]

Maybe some of the packages lay on the installation CD too. I do not know.

Merry Christmas
$ [COLOR="SeaGreen"]xsnow[/COLOR]

---

### Post by moma on 2007-12-19
<duplicate posting. deleted>

---

### Post by thejdev on 2007-12-19
So its not possible to compile a kernel module directly using the gcc command ..... I never knew .... Thanks a lot ...

---

