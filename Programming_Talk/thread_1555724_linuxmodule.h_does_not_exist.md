---
title: "linux/module.h does not exist"
date: 2010-08-18
forum: Programming Talk
---

### Post by tapas_mishra on 2010-08-18
I wrote following program in my home directory.
```

#include <linux/kernel.h>
#include <sys/syscall.h>
#include <linux/module.h>
extern void *sys_table[];
asmlinkage int(*main_sys_exit)(int);
{
        printk("Sys_exit called with err_code=%d\n",err_code);
        return main_sys_exit(err_code);
}

int init_module()
{
        main_sys_exit=sys_table[__NR_exit];
        sys_table[__NR_exit]=alt_exit_function;
}
void cleanup_module()
{
        sys_table[__NR_exit]=main_sys_exit;
}
~      
```

When I compiled it as
```

gcc -Wall -DMODULE -D__KERNEL__  -DLINUX -c sample2.c
```

I got following error 
```

sample2.c:3:26: error: linux/module.h: No such file or directory
sample2.c:5: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘int’
sample2.c:6: error: expected identifier or ‘(’ before ‘{’ token
sample2.c: In function ‘init_module’:
sample2.c:13: error: ‘main_sys_exit’ undeclared (first use in this function)
sample2.c:13: error: (Each undeclared identifier is reported only once
sample2.c:13: error: for each function it appears in.)
sample2.c:14: error: ‘alt_exit_function’ undeclared (first use in this function)
sample2.c:15: warning: control reaches end of non-void function
sample2.c: In function ‘cleanup_module’:
sample2.c:18: error: ‘main_sys_exit’ undeclared (first use in this function)

```

What is the above error and why is it coming?
I did all this in my home directory.

---

### Post by Bachstelze on 2010-08-18
You need to install the headers for your kernel.

```
sudo apt-get install linux-headers-generic
```

---

### Post by tapas_mishra on 2010-08-19
The error is there still```

sudo apt-get install linux-headers-generic
[sudo] password for tapas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 115 not upgraded.
```

I am trying this code from the [link here]("https://docs.google.com/fileview?id=0B2A4urYOAf6POTI1OGE1MjctM2UyMC00OGUzLThlNDUtZDBhOWFjY2Y1MDUz&hl=en")
page number 48 left hand column mentions this code.

---

### Post by interval1066 on 2010-08-19
Might need kernel-package & build-dep (apt-get install both).

---

### Post by tapas_mishra on 2010-08-19
```
tapas@tapas-laptop:/media/disk/Installations/usr/share/doc$ sudo apt-get install build-dep
[sudo] password for tapas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-dep
tapas@tapas-laptop:/media/disk/Installations/usr/share/doc$ sudo apt-get install kernel-dep
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kernel-dep

```

also 
I looked at man page of gcc and searched for
DMODULE D__KERNEL and DLINUX got following

```
Pattern not found  (press RETURN)
```

---

### Post by tapas_mishra on 2010-08-20
I had missed one line of code from the link I gave

following is new program
```

#include <linux/kernel.h>
#include <sys/syscall.h>
#include <linux/module.h>
extern void *sys_table[];
asmlinkage int(*main_sys_exit)(int);
**asmlinkage int alt_exit_function(int err_code)**
{
        printk("Sys_exit called with err_code=%d\n",err_code);
        return main_sys_exit(err_code);
}

int init_module()
{
        main_sys_exit=sys_table[__NR_exit];
        sys_table[__NR_exit]=alt_exit_function;
}
void cleanup_module()
{
        sys_table[__NR_exit]=main_sys_exit;
}

```


```

 gcc -Wall -DMODULE -D__KERNEL -DLINUX -c sample2.c
sample2.c:3:26: error: linux/module.h: No such file or directory
sample2.c:5: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘int’
sample2.c:6: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘int’
sample2.c: In function ‘init_module’:
sample2.c:14: error: ‘main_sys_exit’ undeclared (first use in this function)
sample2.c:14: error: (Each undeclared identifier is reported only once
sample2.c:14: error: for each function it appears in.)
sample2.c:15: error: ‘alt_exit_function’ undeclared (first use in this function)
sample2.c:16: warning: control reaches end of non-void function
sample2.c: In function ‘cleanup_module’:
sample2.c:19: error: ‘main_sys_exit’ undeclared (first use in this function)

```


Now see I think it is easy to tell now as what is the error.
Also
as some one pointed out about linux/module.h

I did a find on module.h

```

/usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h
/usr/src/linux-headers-2.6.28-11/arch/alpha/include/asm/module.h
/usr/src/linux-headers-2.6.28-11/arch/x86/include/asm/module.h
/usr/src/linux-headers-2.6.28-11/arch/sh/include/asm/module.h
/usr/src/linux-headers-2.6.28-11/arch/ia64/include/asm/module.h
/usr/src/linux-headers-2.6.28-11/arch/ia64/include/asm/sn/module.h
/usr/src/linux-headers-2.6.28-11/arch/arm/mach-ns9xxx/include/mach/module.h
/usr/src/linux-headers-2.6.28-11/arch/arm/include/asm/module.h
/usr/src/linux-headers-2.6.28-11/arch/mips/include/asm/module.h
/usr/src/linux-headers-2.6.28-11/arch/avr32/include/asm/module.h
/usr/src/linux-headers-2.6.28-11/arch/sparc/include/asm/module.h
/usr/src/linux-headers-2.6.28-11/arch/s390/include/asm/module.h
/usr/src/linux-headers-2.6.28-11/arch/cris/include/asm/module.h
/usr/src/linux-headers-2.6.28-11/arch/h8300/include/asm/module.h
/usr/src/linux-headers-2.6.28-11/arch/m68knommu/include/asm/module.h
/usr/src/linux-headers-2.6.28-11/arch/blackfin/include/asm/module.h
/usr/src/linux-headers-2.6.28-11/arch/powerpc/include/asm/module.h
/usr/src/linux-headers-2.6.28-11/arch/parisc/include/asm/module.h
/usr/src/linux-headers-2.6.28-11/include/asm-m68k/module.h
/usr/src/linux-headers-2.6.28-11/include/asm-m32r/module.h
/usr/src/linux-headers-2.6.28-11/include/asm-mn10300/module.h
/usr/src/linux-headers-2.6.28-11/include/linux/module.h
/usr/src/linux-headers-2.6.28-11/include/asm-frv/module.h
/usr/src/linux-headers-2.6.28-11/include/asm-xtensa/module.h
/usr/include/sepol/policydb/module.h
/usr/include/sepol/module.h

```

---

### Post by dwhitney67 on 2010-08-20
> **tapas_mishra said:**
> 
What is the above error and why is it coming?

The compiler errors are occurring because you are building the kernel module incorrectly.  You do not build kernel modules in the same fashion as you do regular applications.

What you need is a Makefile to build the module.
For the Makefile:
```

obj-m := sample2.o

KDIR  := /lib/modules/$(shell uname -r)/build

all:
        $(MAKE) -C $(KDIR) M=$(PWD) modules

clean:
        $(MAKE) -C $(KDIR) M=$(PWD) clean

```

---

### Post by tapas_mishra on 2010-08-21
I wrote another module Makefile as follows
```

obj-m+=hello.o
all:
        make -C /lib/modules/$(uname -r)/build/M=$(PWD) modules
clean:
        make -C /lib/modules/$(uname -r)/build/M=$(PWD) clean
clean-files:=Module.symvers

```for the hello world kernel module 
the program is 
```

#include <linux/init.h>
#include <linux/module.h>
MODULE_LICENSE("Dual BSD/GPL");
static int hello_init(void)
 {
        printk(KERN_ALERT "Hello,world tapas\n");
        return 0;
 }
static void hello_exit(void)
 {
        printk(KERN_ALERT "Good Bye,cruel world\n");
 }
module_init(hello_init);
module_exit(hello_exit);

```
The code which is giving me error is on this [link]("https://docs.google.com/fileview?id=0B2A4urYOAf6POTI1OGE1MjctM2UyMC00OGUzLThlNDUtZDBhOWFjY2Y1MDUz&hl=en")
Page 48 left hand side column.


 I also tried 
```
gcc -I /usr/src/linux-headers-2.6.28-11/arch/x86/include/asm/ -I /usr/src/linux-headers-2.6.28-11/include/linux/ -c sample2.c 

```

Got following error
```

sample2.c:3:26: error: linux/module.h: No such file or directory
sample2.c:5: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘int’
sample2.c:6: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘int’
sample2.c: In function ‘init_module’:
sample2.c:14: error: ‘main_sys_exit’ undeclared (first use in this function)
sample2.c:14: error: (Each undeclared identifier is reported only once
sample2.c:14: error: for each function it appears in.)
sample2.c:15: error: ‘alt_exit_function’ undeclared (first use in this function)
sample2.c: In function ‘cleanup_module’:
sample2.c:19: error: ‘main_sys_exit’ undeclared (first use in this function)


```
What more should I try?

---

### Post by tapas_mishra on 2010-08-21
[B][SIZE=2]
[/SIZE][/B]


This is [the link]("http://techblog.aasisvinayak.com/a-voyage-to-kernel-first-24-parts/") from where I am trying these programs.
The author has shared his articles [here.]("https://docs.google.com/fileview?id=0B2A4urYOAf6POTI1OGE1MjctM2UyMC00OGUzLThlNDUtZDBhOWFjY2Y1MDUz&hl=en")You do not need to login to gmail to access any of those docs.Page 48 12th day is what I am trying.
This is the program
```

#include <linux/kernel.h>
 #include <sys/syscall.h>
 #include <linux/module.h>
 extern void *sys_table[];
 asmlinkage int(*main_sys_exit)(int);
 asmlinkage int alt_exit_function(int err_code)
 {
         printk("Sys_exit called with err_code=%d\n",err_code);
         return main_sys_exit(err_code);
 }
 
 int init_module()
 {
         main_sys_exit=sys_table[__NR_ exit];
        sys_table[__NR_exit]=alt_exit_function;
}
void cleanup_module()
{
        sys_table[__NR_exit]=main_sys_exit;

}
```

 To compile it I have tried

 Step1) gcc -Wall -DMODULE -D__KERNEL__  -DLINUX -c sample2.c
 Step2) added -I to gcc flag
   gcc -Wall -DMODULE -D__KERNEL -DLINUX -I
 /usr/src/linux-headers-2.6.28- 11/include/ -c sample2.c

Step3) added one more -I with asm in path
gcc -I /usr/src/linux-headers-2.6.28-11/arch/x86/include/asm/ -I
/usr/src/linux-headers-2.6.28-11/include/ -c sample2.c

Step4)  added asm/x86/include in path
gcc -I /usr/src/linux-headers-2.6.28-11/arch/x86/include/ -I
/usr/src/linux-headers-2.6.28-11/include/ -c sample2.c

Step5)  added linux in -I of second argument
gcc -I /usr/src/linux-headers-2.6.28-11/arch/x86/include/asm/ -I
/usr/src/linux-headers-2.6.28-11/include/linux/ -c sample2.c

Step6)  removed asm from first argument and linux from second
gcc -I /usr/src/linux-headers-2.6.28-11/arch/x86/include/ -I
/usr/src/linux-headers-2.6.28-11/include/ -c sample2.c

All these attempts have failed.
Any guesses?

---

### Post by dwhitney67 on 2010-08-21
> **tapas_mishra said:**
> 
Any guesses?

Read the attached PDF file for more enlightenment...

P.S.  You will need to download and then uncompress the file before you can peruse it.
```

gunzip linux-kernel-modules-tutorial.pdf.gz

```

---

### Post by tapas_mishra on 2010-08-30
I have read it but I tried a Makefile 
```


obj-m += sample2.o
all: 
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean: 
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

```
The above Makefile worked with some warning.
```

make -C /lib/modules/2.6.28-11-generic/build M=/home/tapas/exer modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/tapas/exer/sample21.o
/home/tapas/exer/sample21.c: In function &#8216;init_module&#8217;:
/home/tapas/exer/sample21.c:17: warning: control reaches end of non-void function
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "sys_table" [/home/tapas/exer/sample21.ko] undefined!
  CC      /home/tapas/exer/sample21.mod.o
  LD [M]  /home/tapas/exer/sample21.ko
```

but the method of gcc has not worked.
Where as the program given in the link I gave is 
```

#include <linux/kernel.h>
#include <linux/module.h>
#include <sys/syscall.h>
extern void *sys_table[];
asmlinkage int(*main_sys_exit)(int);
asmlinkage int alt_exit_function(int err_code)
{
        printk("Sys_exit called with err_code=%d\n",err_code);
        return main_sys_exit(err_code);
}

int init_module()
{
        main_sys_exit=sys_table[__NR_exit];
        sys_table[__NR_exit]=alt_exit_function;
}
void cleanup_module()
{
        sys_table[__NR_exit]=main_sys_exit;
}
```

I have tried


 the Makefile 
```

obj-m += sample2.o
all: 
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean: 
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```
also failed with following errors
```

make -C /lib/modules/2.6.28-11-generic/build M=/home/tapas/exer modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/tapas/exer/sample2.o
/home/tapas/exer/sample2.c:3:25: error: sys/syscall.h: No such file or directory
/home/tapas/exer/sample2.c: In function &#8216;init_module&#8217;:
/home/tapas/exer/sample2.c:14: error: &#8216;__NR_exit&#8217; undeclared (first use in this function)
/home/tapas/exer/sample2.c:14: error: (Each undeclared identifier is reported only once
/home/tapas/exer/sample2.c:14: error: for each function it appears in.)
/home/tapas/exer/sample2.c: In function &#8216;cleanup_module&#8217;:
/home/tapas/exer/sample2.c:19: error: &#8216;__NR_exit&#8217; undeclared (first use in this function)
make[2]: *** [/home/tapas/exer/sample2.o] Error 1
make[1]: *** [_module_/home/tapas/exer] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [all] Error 2
```

also following approach of gcc ```

gcc -I /usr/src/linux-headers-`uname -r`/include -I /usr/src/linux-headers-`uname -r`/arch/x86/include/asm -I /usr/include -Wall -DMODULE -D__KERNEL__ -DLINUX -c samp\le2.c

```

but then in this  method also there were errors as following
```

In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/kernel.h:11,
                 from sample2.c:1:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/linkage.h:5:25: error: asm/linkage.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/kernel.h:15,
                 from sample2.c:1:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitops.h:17:24: error: asm/bitops.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/kernel.h:15,
                 from sample2.c:1:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitops.h: In function &#8216;get_bitmask_order&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitops.h:29: warning: implicit declaration of function &#8216;fls&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitops.h: In function &#8216;hweight_long&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitops.h:45: warning: implicit declaration of function &#8216;hweight32&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitops.h:45: warning: implicit declaration of function &#8216;hweight64&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitops.h: In function &#8216;fls_long&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitops.h:112: warning: implicit declaration of function &#8216;fls64&#8217;
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/kernel.h:16,
                 from sample2.c:1:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/log2.h: At top level:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/log2.h:52: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;is_power_of_2&#8217;
In file included from sample2.c:1:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/kernel.h:21:21: error: asm/bug.h: No such file or directory
In file included from sample2.c:1:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/kernel.h:167: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/kernel.h:168: error: format string argument not a string type
/usr/src/linux-headers-2.6.28-11-generic/include/linux/kernel.h:167: warning: conflicting types for built-in function &#8216;snprintf&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/kernel.h:169: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/kernel.h:169: warning: conflicting types for built-in function &#8216;vsnprintf&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/kernel.h:171: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/kernel.h:172: error: format string argument not a string type
/usr/src/linux-headers-2.6.28-11-generic/include/linux/kernel.h:173: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/kernel.h:236: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;printk_timed_ratelimit&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/kernel.h:301: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/kernel.h:303: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/kernel.h:303: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;bool&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/kernel.h:306: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/kernel.h:306: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;bool&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/kernel.h:308: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/list.h:6,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:9,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/prefetch.h:14:27: error: asm/processor.h: No such file or directory
/usr/src/linux-headers-2.6.28-11-generic/include/linux/prefetch.h:15:23: error: asm/cache.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/list.h:6,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:9,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/prefetch.h:53: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:9,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/list.h:7:24: error: asm/system.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/preempt.h:9,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/spinlock.h:50,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/seqlock.h:29,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:8,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/stat.h:60,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:10,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h:34: error: expected specifier-qualifier-list before &#8216;clockid_t&#8217;
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/preempt.h:9,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/spinlock.h:50,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/seqlock.h:29,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:8,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/stat.h:60,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:10,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h:55:29: error: asm/thread_info.h: No such file or directory
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h:64: warning: &#8216;struct thread_info&#8217; declared inside parameter list
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h:64: warning: its scope is only this definition or declaration, which is probably not what you want
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h: In function &#8216;set_ti_thread_flag&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h:66: warning: implicit declaration of function &#8216;set_bit&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h:66: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h: At top level:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h:69: warning: &#8216;struct thread_info&#8217; declared inside parameter list
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h: In function &#8216;clear_ti_thread_flag&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h:71: warning: implicit declaration of function &#8216;clear_bit&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h:71: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h: At top level:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h:74: warning: &#8216;struct thread_info&#8217; declared inside parameter list
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h: In function &#8216;test_and_set_ti_thread_flag&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h:76: warning: implicit declaration of function &#8216;test_and_set_bit&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h:76: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h: At top level:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h:79: warning: &#8216;struct thread_info&#8217; declared inside parameter list
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h: In function &#8216;test_and_clear_ti_thread_flag&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h:81: warning: implicit declaration of function &#8216;test_and_clear_bit&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h:81: error: dereferencing pointer to incomplete type
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h: At top level:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h:84: warning: &#8216;struct thread_info&#8217; declared inside parameter list
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h: In function &#8216;test_ti_thread_flag&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h:86: warning: implicit declaration of function &#8216;test_bit&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/thread_info.h:86: error: dereferencing pointer to incomplete type
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/seqlock.h:29,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:8,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/stat.h:60,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:10,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/spinlock.h:348:24: error: asm/atomic.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/seqlock.h:29,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:8,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/stat.h:60,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:10,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/spinlock.h: At top level:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/spinlock.h:357: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:8,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/stat.h:60,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:10,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/seqlock.h: In function &#8216;write_seqlock&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/seqlock.h:64: warning: implicit declaration of function &#8216;smp_wmb&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/seqlock.h: In function &#8216;read_seqbegin&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/seqlock.h:92: warning: implicit declaration of function &#8216;smp_rmb&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/seqlock.h:94: warning: implicit declaration of function &#8216;cpu_relax&#8217;
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:9,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/stat.h:60,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:10,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/math64.h:5:23: error: asm/div64.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:9,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/stat.h:60,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:10,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/math64.h: In function &#8216;div_u64&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/math64.h:69: warning: implicit declaration of function &#8216;div_u64_rem&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/math64.h: In function &#8216;div_s64&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/math64.h:80: warning: implicit declaration of function &#8216;div_s64_rem&#8217;
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/stat.h:60,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:10,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h: At top level:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:15: error: expected specifier-qualifier-list before &#8216;time_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:21: error: expected specifier-qualifier-list before &#8216;time_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h: In function &#8216;timespec_equal&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:48: error: &#8216;const struct timespec&#8217; has no member named &#8216;tv_sec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:48: error: &#8216;const struct timespec&#8217; has no member named &#8216;tv_sec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:48: error: &#8216;const struct timespec&#8217; has no member named &#8216;tv_nsec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:48: error: &#8216;const struct timespec&#8217; has no member named &#8216;tv_nsec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:49: warning: control reaches end of non-void function
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h: In function &#8216;timespec_compare&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:58: error: &#8216;const struct timespec&#8217; has no member named &#8216;tv_sec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:58: error: &#8216;const struct timespec&#8217; has no member named &#8216;tv_sec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:60: error: &#8216;const struct timespec&#8217; has no member named &#8216;tv_sec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:60: error: &#8216;const struct timespec&#8217; has no member named &#8216;tv_sec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:62: error: &#8216;const struct timespec&#8217; has no member named &#8216;tv_nsec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:62: error: &#8216;const struct timespec&#8217; has no member named &#8216;tv_nsec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:63: warning: control reaches end of non-void function
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h: In function &#8216;timeval_compare&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:67: error: &#8216;const struct timeval&#8217; has no member named &#8216;tv_sec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:67: error: &#8216;const struct timeval&#8217; has no member named &#8216;tv_sec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:69: error: &#8216;const struct timeval&#8217; has no member named &#8216;tv_sec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:69: error: &#8216;const struct timeval&#8217; has no member named &#8216;tv_sec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:71: error: &#8216;const struct timeval&#8217; has no member named &#8216;tv_usec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:71: error: &#8216;const struct timeval&#8217; has no member named &#8216;tv_usec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:72: warning: control reaches end of non-void function
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h: At top level:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:78: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;time_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h: In function &#8216;timespec_sub&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:89: error: &#8216;struct timespec&#8217; has no member named &#8216;tv_sec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:89: error: &#8216;struct timespec&#8217; has no member named &#8216;tv_sec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:90: error: &#8216;struct timespec&#8217; has no member named &#8216;tv_nsec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:90: error: &#8216;struct timespec&#8217; has no member named &#8216;tv_nsec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:90: error: too many arguments to function &#8216;set_normalized_timespec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h: In function &#8216;timespec_to_ns&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:148: error: &#8216;const struct timespec&#8217; has no member named &#8216;tv_sec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:148: error: &#8216;const struct timespec&#8217; has no member named &#8216;tv_nsec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:149: warning: control reaches end of non-void function
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h: In function &#8216;timeval_to_ns&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:160: error: &#8216;const struct timeval&#8217; has no member named &#8216;tv_sec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:161: error: &#8216;const struct timeval&#8217; has no member named &#8216;tv_usec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:162: warning: control reaches end of non-void function
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h: In function &#8216;timespec_add_ns&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:190: error: &#8216;struct timespec&#8217; has no member named &#8216;tv_sec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:190: error: &#8216;struct timespec&#8217; has no member named &#8216;tv_nsec&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/time.h:191: error: &#8216;struct timespec&#8217; has no member named &#8216;tv_nsec&#8217;
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:10,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/stat.h: At top level:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/stat.h:64: error: expected specifier-qualifier-list before &#8216;dev_t&#8217;
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:9,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:13,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/wait.h:26:25: error: asm/current.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:8,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/nodemask.h:89,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:16,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:13,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/string.h:19:24: error: asm/string.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:8,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/nodemask.h:89,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:16,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:13,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/string.h:28: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;strlcpy&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/string.h:37: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;strlcat&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/string.h:52: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/string.h:52: warning: conflicting types for built-in function &#8216;strncasecmp&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/string.h:58: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/string.h:106: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/string.h:107: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/string.h:112: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;sysfs_streq&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/string.h:114: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;memory_read_from_buffer&#8217;
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/nodemask.h:89,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:16,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:13,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h: In function &#8216;bitmap_zero&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:142: error: &#8216;BITS_PER_LONG&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:142: error: (Each undeclared identifier is reported only once
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:142: error: for each function it appears in.)
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h: In function &#8216;bitmap_fill&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:152: error: &#8216;size_t&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:152: error: expected &#8216;;&#8217; before &#8216;nlongs&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:153: error: &#8216;nlongs&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:157: error: &#8216;BITS_PER_LONG&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h: In function &#8216;bitmap_copy&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:163: error: &#8216;BITS_PER_LONG&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h: In function &#8216;bitmap_and&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:174: error: &#8216;BITS_PER_LONG&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h: In function &#8216;bitmap_or&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:183: error: &#8216;BITS_PER_LONG&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h: In function &#8216;bitmap_xor&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:192: error: &#8216;BITS_PER_LONG&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h: In function &#8216;bitmap_andnot&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:201: error: &#8216;BITS_PER_LONG&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h: In function &#8216;bitmap_complement&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:210: error: &#8216;BITS_PER_LONG&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h: In function &#8216;bitmap_equal&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:219: error: &#8216;BITS_PER_LONG&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:223: warning: control reaches end of non-void function
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h: In function &#8216;bitmap_intersects&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:228: error: &#8216;BITS_PER_LONG&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:232: warning: control reaches end of non-void function
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h: In function &#8216;bitmap_subset&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:237: error: &#8216;BITS_PER_LONG&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:241: warning: control reaches end of non-void function
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h: In function &#8216;bitmap_empty&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:245: error: &#8216;BITS_PER_LONG&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:249: warning: control reaches end of non-void function
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h: In function &#8216;bitmap_full&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:253: error: &#8216;BITS_PER_LONG&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:257: warning: control reaches end of non-void function
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h: In function &#8216;bitmap_weight&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:261: error: &#8216;BITS_PER_LONG&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h: In function &#8216;bitmap_shift_right&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:269: error: &#8216;BITS_PER_LONG&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h: In function &#8216;bitmap_shift_left&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/bitmap.h:278: error: &#8216;BITS_PER_LONG&#8217; undeclared (first use in this function)
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:16,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:13,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/nodemask.h: In function &#8216;__first_node&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/nodemask.h:233: warning: implicit declaration of function &#8216;find_first_bit&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/nodemask.h: In function &#8216;__next_node&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/nodemask.h:239: warning: implicit declaration of function &#8216;find_next_bit&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/nodemask.h: In function &#8216;__first_unset_node&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/nodemask.h:257: warning: implicit declaration of function &#8216;find_first_zero_bit&#8217;
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:13,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:20:22: error: asm/page.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:13,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h: At top level:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:333: error: expected specifier-qualifier-list before &#8216;atomic_long_t&#8217;
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/notifier.h:13,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/memory_hotplug.h:6,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:640,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:13,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mutex.h:50: error: expected specifier-qualifier-list before &#8216;atomic_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mutex.h: In function &#8216;mutex_is_locked&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mutex.h:117: warning: implicit declaration of function &#8216;atomic_read&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mutex.h:117: error: &#8216;struct mutex&#8217; has no member named &#8216;count&#8217;
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/notifier.h:14,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/memory_hotplug.h:6,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:640,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:13,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/rwsem.h:22:65: error: asm/rwsem.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/memory_hotplug.h:6,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:640,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:13,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/notifier.h: At top level:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/notifier.h:62: error: field &#8216;rwsem&#8217; has incomplete type
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:13,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h: In function &#8216;populated_zone&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:673: error: &#8216;struct zone&#8217; has no member named &#8216;present_pages&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:674: warning: control reaches end of non-void function
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h: In function &#8216;is_normal&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:722: error: &#8216;struct zone&#8217; has no member named &#8216;zone_pgdat&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:723: warning: control reaches end of non-void function
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h: At top level:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:747: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:747: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;loff_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:750: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:750: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;loff_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:752: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:752: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;loff_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:754: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:754: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;loff_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:756: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:756: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;loff_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:759: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:759: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;loff_t&#8217;
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/topology.h:30,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:763,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:13,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/cpumask.h:279: error: &#8216;BITS_PER_LONG&#8217; undeclared here (not in a function)
/usr/src/linux-headers-2.6.28-11-generic/include/linux/cpumask.h:821: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;cpumask_equal&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/cpumask.h:833: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;cpumask_intersects&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/cpumask.h:856: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;cpumask_empty&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/cpumask.h:865: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;cpumask_full&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/cpumask.h:972: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;cpumask_size&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/cpumask.h:1006: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;alloc_cpumask_var&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/cpumask.h:1039: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;bool&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/cpumask.h: In function &#8216;set_cpu_possible&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/cpumask.h:1041: error: &#8216;possible&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.28-11-generic/include/linux/cpumask.h: At top level:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/cpumask.h:1047: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;bool&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/cpumask.h: In function &#8216;set_cpu_present&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/cpumask.h:1049: error: &#8216;present&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.28-11-generic/include/linux/cpumask.h: At top level:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/cpumask.h:1055: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;bool&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/cpumask.h: In function &#8216;set_cpu_online&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/cpumask.h:1057: error: &#8216;online&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.28-11-generic/include/linux/cpumask.h: At top level:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/cpumask.h:1063: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;bool&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/cpumask.h: In function &#8216;set_cpu_active&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/cpumask.h:1065: error: &#8216;active&#8217; undeclared (first use in this function)
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/mmzone.h:763,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:13,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/topology.h:34:26: error: asm/topology.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:13,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/gfp.h: In function &#8216;allocflags_to_migratetype&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/gfp.h:110: warning: implicit declaration of function &#8216;WARN_ON&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/gfp.h: In function &#8216;alloc_pages_node&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/gfp.h:203: warning: implicit declaration of function &#8216;cpu_to_node&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/gfp.h: At top level:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/gfp.h:231: error: expected &#8216;)&#8217; before &#8216;size&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/gfp.h:232: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:14,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/elf.h:7:21: error: asm/elf.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:14,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/elf.h:402: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;loff_t&#8217;
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/kobject.h:21,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:16,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/sysfs.h:31: error: expected specifier-qualifier-list before &#8216;mode_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/sysfs.h:36: error: expected specifier-qualifier-list before &#8216;mode_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/sysfs.h:67: error: expected specifier-qualifier-list before &#8216;size_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/sysfs.h:78: error: expected specifier-qualifier-list before &#8216;ssize_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/sysfs.h:167: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;mode_t&#8217;
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/kobject.h:24,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:16,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/kref.h:22: error: expected specifier-qualifier-list before &#8216;atomic_t&#8217;
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:16,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/kobject.h:126: error: expected specifier-qualifier-list before &#8216;ssize_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/kobject.h:221: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/percpu.h:5,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/rcupdate.h:39,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/tracepoint.h:18,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:19,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/slab.h:87: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/slab.h:87: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/slab.h:127: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/slab.h:128: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/slab.h:130: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;ksize&#8217;
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/slab.h:156,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/percpu.h:5,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/rcupdate.h:39,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/tracepoint.h:18,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:19,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/slab_def.h:20: error: expected specifier-qualifier-list before &#8216;size_t&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/slab_def.h:29: error: expected &#8216;)&#8217; before &#8216;size&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/slab_def.h:31: error: expected &#8216;)&#8217; before &#8216;size&#8217;
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/percpu.h:5,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/rcupdate.h:39,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/tracepoint.h:18,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:19,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/slab.h:210: error: expected &#8216;)&#8217; before &#8216;n&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/slab.h:228: error: expected &#8216;)&#8217; before &#8216;size&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/slab.h:233: error: expected &#8216;)&#8217; before &#8216;size&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/slab.h:303: error: expected &#8216;)&#8217; before &#8216;size&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/slab.h:314: error: expected &#8216;)&#8217; before &#8216;size&#8217;
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/rcupdate.h:39,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/tracepoint.h:18,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:19,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/percpu.h:9:24: error: asm/percpu.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/rcupdate.h:39,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/tracepoint.h:18,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:19,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/percpu.h:91: error: expected &#8216;)&#8217; before &#8216;size&#8217;
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/rcupdate.h:43,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/tracepoint.h:18,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:19,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/completion.h:86: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;try_wait_for_completion&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/completion.h:87: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;completion_done&#8217;
In file included from /usr/src/linux-headers-2.6.28-11-generic/include/linux/rcupdate.h:58,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/tracepoint.h:18,
                 from /usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:19,
                 from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/rcupreempt.h:51: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;rcu_dyntick_sched&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/rcupreempt.h:51: warning: data definition has no type or storage class
/usr/src/linux-headers-2.6.28-11-generic/include/linux/rcupreempt.h:51: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;DECLARE_PER_CPU&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/rcupreempt.h: In function &#8216;rcu_qsctr_inc&#8217;:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/rcupreempt.h:55: warning: implicit declaration of function &#8216;per_cpu&#8217;
/usr/src/linux-headers-2.6.28-11-generic/include/linux/rcupreempt.h:55: error: &#8216;rcu_dyntick_sched&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.28-11-generic/include/linux/rcupreempt.h:55: error: lvalue required as unary &#8216;&&#8217; operand
In file included from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:20:23: error: asm/local.h: No such file or directory
/usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:22:24: error: asm/module.h: No such file or directory
In file included from sample2.c:2:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h: At top level:
/usr/src/linux-headers-2.6.28-11-generic/include/linux/module.h:50: error: expected specifier-qualifier-list before &#8216;ssize_t&#8217;
sample2.c: In function &#8216;init_module&#8217;:
sample2.c:16: warning: control reaches end of non-void function
```

---

### Post by dwhitney67 on 2010-08-30
The function init_module() needs to return a value; after all, you have declared it to return an int.  Try returning 0.
```

static int __init init_module(void)
{
   ...

   return 0;
}

```
And as for the other warning, from what I have read (last week), the sys_table[] is no longer accessible (hence not defined) in kernel versions 2.6.x.  Maybe a security feature?

Pay careful attention to the documentation that you are referencing to develop your code since a lot changed between 2.4.x and 2.6.x of the Linux kernel.

The most basic of kernel module source code for 2.6.x kernels should look something like:
```

#include <linux/module.h>      // Needed by all modules

#define DRIVER_AUTHOR "Your Name"
#define DRIVER_DESC   "A Hello World kernel module."

MODULE_LICENSE("GPL");
MODULE_AUTHOR(DRIVER_AUTHOR);            /* Who wrote this module? */
MODULE_DESCRIPTION(DRIVER_DESC);         /* What does this module do */


static int __init hello_world(void)
{
  printk("hello world\n");
  return 0;
}

static void __exit goodbye_world(void)
{
  printk("goodbye world\n");
}

module_init( hello_world );
module_exit( goodbye_world );

```
Your Makefile is correct.

---

