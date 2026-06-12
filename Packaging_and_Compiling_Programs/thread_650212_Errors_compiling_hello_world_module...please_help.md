---
title: "Errors compiling hello world module...please help"
date: 2007-12-26
forum: Packaging and Compiling Programs
---

### Post by rabantu on 2007-12-26
Hi All,

I have installed Xubuntu 7.04, i guess. It has 2.6.20.16 kernel. Then I got 2.6.22.1 kernel source code and compiled it( after lots of issues though). It compiled and I am able to boot into it as well. Now , my next venture is to compile the simple Hello World sample from "Linux Device Drivers" by Jonathan Corbett et. all.

When I compile the helloworld.c, I am getting the following errors:

-desktop:~/mysamples/sample1$ make
gcc -D__KERNEL__ -I~/linux-2.6.22.1/include -c helloworld.c -o hello.o
In file included from ~/linux-2.6.22.1/include/asm/thread_info.h:16,
from ~/linux-2.6.22.1/include/linux/thread_info.h:21,
from ~/linux-2.6.22.1/include/linux/preempt.h:9,
from ~/linux-2.6.22.1/include/linux/spinlock.h:49,
from ~/linux-2.6.22.1/include/linux/module.h:9,
from helloworld.c:2:
~/linux-2.6.22.1/include/asm/processor.h:83: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
~/linux-2.6.22.1/include/asm/processor.h:83: error: requested alignment is not a constant
In file included from ~/linux-2.6.22.1/include/linux/module.h:21,
from helloworld.c:2:
~/linux-2.6.22.1/include/asm/module.h:64:2: error: #error unknown processor family
make: *** [hello.o] Error 1

I googled aa lot on this and got some kind of insight into it. Most posts suggested that it's some kind of mismatch of header files. I tried different things none of them seems to work...it's like shooting in the dark.
Can someone please point me in the right direction?

Thanks in advance,
rabantu

---

### Post by amaresh_83 on 2007-12-26
Hi,
        install library package in your system.
        
        sudo apt-get install build-essential
or (if superuser)
      apt-get install build-essential

might be now you will get your result

---

### Post by rabantu on 2007-12-26
> **amaresh_83 said:**
> Hi,
        install library package in your system.
        
        sudo apt-get install build-essential
or (if superuser)
      apt-get install build-essential

might be now you will get your result

hi Amareesh,

Thanks for the reply. I already have the build-essential ( I had issues building my kernel...so i had to get the build-essential package after which I could successfully build the kernel )
But, I am not able compile this hello world module program.
So, what else?? Any other ideas?

Now, I am going to try simple hello world sample to see if I can build a c program at all

-Thanks,

---

### Post by danellisuk on 2008-03-14
I have the same error also.  I am following the hello kernel example from Beginning Linux Programming (Wrox).

I am using the following build command:-

```
gcc -D__KERNEL__ -D__SMP__ -DMODULE -DMODVERSIONS -I/usr/src/linux-headers-2.6.22-14-generic/include -Wall -O2 -o module.o -c hello.c
```

Here are the first few lines of the errors (presuming they are most relevant)

```
In file included from /usr/src/linux-headers-2.6.22-14-generic/include/asm/thread_info.h:16,
                 from /usr/src/linux-headers-2.6.22-14-generic/include/linux/thread_info.h:21,
                 from /usr/src/linux-headers-2.6.22-14-generic/include/linux/preempt.h:9,
                 from /usr/src/linux-headers-2.6.22-14-generic/include/linux/spinlock.h:49,
                 from /usr/src/linux-headers-2.6.22-14-generic/include/linux/module.h:9,
                 from hello.c:1:
/usr/src/linux-headers-2.6.22-14-generic/include/asm/processor.h:83: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/usr/src/linux-headers-2.6.22-14-generic/include/asm/processor.h:83: error: requested alignment is not a constant
/usr/src/linux-headers-2.6.22-14-generic/include/asm/processor.h: In function ‘cpuid_count’:

```

I am using Ubuntu 7.10 and I have build-essential.  Did you ever find the solution to this problem?

---

### Post by dalonso on 2008-03-14
I believe many things have changed since this wrox book was written. In fact, I think that there are some needed environment variables that you should put in order to build a kernel module, some of them controlling the architecture the module is being built.

Please try the the attached archive. Simply, untargz, and make inside main directory.

The source code for the hello module is inside the src directory. After build you both will find the module hello.ko inside the src directory.

---

### Post by danellisuk on 2008-04-04
That was fantastic, thank you very much.  I couldn't have received a more complete answer to my question.

'sudo make install' failed, but I was able to insert and remove the module with

```

sudo insmod ./src/hello.ko
sudo rmmod hello

```

I could then see the messages with

```

dmesg | tail
[ 1382.956000] Hello world 1.
[ 1865.596000] Goodbye world 1.

```

Now, I just have to find something useful to attempt myself!

I have the 3rd edition of 'Beginning Linux Programming' which I purchased not long ago, I have just seen that there is now a new 4th edition.  However, can you recommend any other books? I normally get on very well with Wrox books (typically c#, asp.net etc) but I am struggling a little with this one, so I am uncertain whether to buy the 4th edition.

Well, thanks for your reply, it is much appreciated.

Regards,
Daniel Ellis.

---

### Post by katiagiovannini on 2009-04-28
Hi, 
I have the same problem but even if I tried to resolve downloading the tar gz and doing make in the main folder I have this message:

```

make -C /lib/modules/2.6.11.11/build M=/src/libro/sample-module V=0 modules
make[1]: Entering directory `/usr/src/linux-2.6.11.11'
  CC [M]  /src/libro/sample-module/src/hello.o
In file included from include/linux/module.h:9,
                 from /src/libro/sample-module/src/hello.c:4:
include/linux/config.h:4:28: linux/autoconf.h: No such file or directory
In file included from include/asm/thread_info.h:17,
                 from include/linux/thread_info.h:21,
                 from include/linux/spinlock.h:12,
                 from include/linux/capability.h:45,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /src/libro/sample-module/src/hello.c:4:
include/asm/processor.h:69: error: `CONFIG_X86_L1_CACHE_SHIFT' undeclared here (not in a function)
include/asm/processor.h:69: error: requested alignment is not a constant
In file included from include/linux/list.h:7,
                 from include/linux/wait.h:23,
                 from include/asm/semaphore.h:41,
                 from include/linux/sched.h:19,
                 from include/linux/module.h:10,
                 from /src/libro/sample-module/src/hello.c:4:
include/linux/prefetch.h: In function `prefetch_range':
include/linux/prefetch.h:64: error: `CONFIG_X86_L1_CACHE_SHIFT' undeclared (first use in this function)
include/linux/prefetch.h:64: error: (Each undeclared identifier is reported only once
include/linux/prefetch.h:64: error: for each function it appears in.)
In file included from include/linux/module.h:23,
                 from /src/libro/sample-module/src/hello.c:4:
include/asm/module.h:56:2: #error unknown processor family
make[3]: *** [/src/libro/sample-module/src/hello.o] Error 1
make[2]: *** [/src/libro/sample-module/src] Error 2
make[1]: *** [_module_/src/libro/sample-module] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.11.11'
make: *** [all] Error 2

```I hope that someone have the answer.. 
Thank you

---

