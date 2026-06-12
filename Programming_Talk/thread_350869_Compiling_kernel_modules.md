---
title: "Compiling kernel modules"
date: 2007-02-01
forum: Programming Talk
---

### Post by pc.bijl on 2007-02-01
Hi,

I want to write an kernel module that filters network packets (in a special way).
But when I compile the most simples kernel module:
```
#define __KERNEL__
#define MODULE

#include <linux/module.h>
#include <linux/kernel.h>
int init_module(void)
{
  /* do something to initialize the module */
  return 0; /* on error, return -EERR */
}
void cleanup_module(void)
{
  /* cleanup after the module */
}
```

And I compile this: I get some weired errors
```
pieter@pieter-desktop:~/prog/network/netfilter_way$ gcc drop.c -c -I /usr/src/linux-headers-2.6.17-10/include/ 
In file included from /usr/src/linux-headers-2.6.17-10/include/asm/thread_info.h:16,
                 from /usr/src/linux-headers-2.6.17-10/include/linux/thread_info.h:21,
                 from /usr/src/linux-headers-2.6.17-10/include/linux/preempt.h:9,
                 from /usr/src/linux-headers-2.6.17-10/include/linux/spinlock.h:49,
                 from /usr/src/linux-headers-2.6.17-10/include/linux/capability.h:45,
                 from /usr/src/linux-headers-2.6.17-10/include/linux/sched.h:44,
                 from /usr/src/linux-headers-2.6.17-10/include/linux/module.h:9,
                 from drop.c:4:
/usr/src/linux-headers-2.6.17-10/include/asm/processor.h:76: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/usr/src/linux-headers-2.6.17-10/include/asm/processor.h:76: error: requested alignment is not a constant
In file included from /usr/src/linux-headers-2.6.17-10/include/linux/sched.h:49,
                 from /usr/src/linux-headers-2.6.17-10/include/linux/module.h:9,
                 from drop.c:4:
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:33:3: error: #error You lose.
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:210:31: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:254:46: error: division by zero in #if
In file included from /usr/src/linux-headers-2.6.17-10/include/linux/sched.h:49,
                 from /usr/src/linux-headers-2.6.17-10/include/linux/module.h:9,
                 from drop.c:4:
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h: In function ‘jiffies_to_msecs’:
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:259: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:259: error: (Each undeclared identifier is reported only once
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:259: error: for each function it appears in.)
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:265:46: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h: In function ‘jiffies_to_usecs’:
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:270: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:278:46: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h: In function ‘msecs_to_jiffies’:
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:283: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:291:46: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h: In function ‘usecs_to_jiffies’:
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:296: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h: In function ‘timespec_to_jiffies’:
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:315: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:321: error: ‘SHIFT_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h: In function ‘jiffies_to_timespec’:
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:334: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h: In function ‘timeval_to_jiffies’:
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:356: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:360: error: ‘SHIFT_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h: In function ‘jiffies_to_timeval’:
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:372: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:385:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h: In function ‘jiffies_to_clock_t’:
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:386: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h: In function ‘clock_t_to_jiffies’:
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:397: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:416:6: error: division by zero in #if
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h: In function ‘jiffies_64_to_clock_t’:
/usr/src/linux-headers-2.6.17-10/include/linux/jiffies.h:417: error: ‘CONFIG_HZ’ undeclared (first use in this function)
In file included from /usr/src/linux-headers-2.6.17-10/include/linux/rwsem.h:26,
                 from /usr/src/linux-headers-2.6.17-10/include/asm/semaphore.h:42,
                 from /usr/src/linux-headers-2.6.17-10/include/linux/sched.h:57,
                 from /usr/src/linux-headers-2.6.17-10/include/linux/module.h:9,
                 from drop.c:4:
/usr/src/linux-headers-2.6.17-10/include/asm/rwsem.h: In function ‘__down_read’:
/usr/src/linux-headers-2.6.17-10/include/asm/rwsem.h:105: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/usr/src/linux-headers-2.6.17-10/include/asm/rwsem.h: In function ‘__down_write’:
/usr/src/linux-headers-2.6.17-10/include/asm/rwsem.h:157: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/usr/src/linux-headers-2.6.17-10/include/asm/rwsem.h: In function ‘__up_read’:
/usr/src/linux-headers-2.6.17-10/include/asm/rwsem.h:194: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/usr/src/linux-headers-2.6.17-10/include/asm/rwsem.h: In function ‘__up_write’:
/usr/src/linux-headers-2.6.17-10/include/asm/rwsem.h:220: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/usr/src/linux-headers-2.6.17-10/include/asm/rwsem.h: In function ‘__downgrade_write’:
/usr/src/linux-headers-2.6.17-10/include/asm/rwsem.h:245: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
In file included from /usr/src/linux-headers-2.6.17-10/include/linux/sched.h:57,
                 from /usr/src/linux-headers-2.6.17-10/include/linux/module.h:9,
                 from drop.c:4:
/usr/src/linux-headers-2.6.17-10/include/asm/semaphore.h: In function ‘down’:
/usr/src/linux-headers-2.6.17-10/include/asm/semaphore.h:105: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/usr/src/linux-headers-2.6.17-10/include/asm/semaphore.h: In function ‘down_interruptible’:
/usr/src/linux-headers-2.6.17-10/include/asm/semaphore.h:130: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/usr/src/linux-headers-2.6.17-10/include/asm/semaphore.h: In function ‘down_trylock’:
/usr/src/linux-headers-2.6.17-10/include/asm/semaphore.h:155: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/usr/src/linux-headers-2.6.17-10/include/asm/semaphore.h: In function ‘up’:
/usr/src/linux-headers-2.6.17-10/include/asm/semaphore.h:179: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
In file included from /usr/src/linux-headers-2.6.17-10/include/linux/module.h:22,
                 from drop.c:4:
/usr/src/linux-headers-2.6.17-10/include/asm/module.h:60:2: error: #error unknown processor family
pieter@pieter-desktop:~/prog/network/netfilter_way$ 
```

Can someone say what I am doing wrong?

My excuse for my bad English,
Pieter

---

### Post by pc.bijl on 2007-02-02
Ok, now finally I found an solution to it. Do not compile by your self, but with an make file redirecting to the kernel modules dir:

```

obj-m += micro_firewall.o

all:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

```

---

### Post by rabantu on 2007-12-26
> **pc.bijl said:**
> Ok, now finally I found an solution to it. Do not compile by your self, but with an make file redirecting to the kernel modules dir:

```

obj-m += micro_firewall.o

all:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

```

Hi Pieter,
I am having similar issues and am struggling with this for the past couple of days: confused:

Could you please explain how you resolved this issue a little bit more elaborately?

Thanks in advance

---

### Post by moma on 2007-12-27
Meditate also over [ this example...]("http://ubuntuforums.org/showthread.php?p=3486457#post3486457")

+ study these kernel developers' guides
[http://www.futuredesktop.org/kernel.html](http://www.futuredesktop.org/kernel.html) 
Section: Driver and module programming.

@pc.bijl says that create a **Makefile** and compile your code with 
$ make

---

### Post by kvorion on 2007-12-27
> **rabantu said:**
> Hi Pieter,
I am having similar issues and am struggling with this for the past couple of days: confused:

Could you please explain how you resolved this issue a little bit more elaborately?

Thanks in advance

what exactly is the problem that you are facing?

---

