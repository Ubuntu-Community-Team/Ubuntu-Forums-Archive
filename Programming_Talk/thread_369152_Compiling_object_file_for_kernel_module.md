---
title: "Compiling object file for kernel module"
date: 2007-02-24
forum: Programming Talk
---

### Post by yannifan on 2007-02-24
Hello ppl,

   I have a problem in compiling a kernel source. Iis a basic Hello world source...
I installed kernel source tree in /usr/src/linux-source-2.6.15.x

The hello.c file is placed in a home directory... The command for compiling used is 
 a) gcc -D__KERNEL__ -I /usr/src/linux-source-2.6.15/include -DMODULE -c hello.c -o hello.o
 b) gcc -D__KERNEL__ -I /usr/include -DMODULE -c hello.c -o hello.o

Hello.c is in the present working dir... Command a refers the kernel tree got from kernel.org
Command b uses the include files present in Ubuntu by default.

The errors are : 
for a) /usr/include/linux/types.h:4:23: error: sys/types.h: No such file or directory
/usr/include/linux/types.h:4:23: error: sys/types.h: No such file or directory
 /usr/include/asm-i386/page.h:4:20: error: unistd.h: No such file or directory
/usr/include/linux/signal.h:4:20: error: signal.h: No such file or directory
In file included from /usr/include/linux/module.h:9,
                 from hello.c:2:
/usr/include/linux/sched.h:77:22: error: sys/time.h: No such file or directory
In file included from hello.c:2:



for b) 
/usr/include/linux/types.h:4:23: error: sys/types.h: No such file or directory
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/asm/posix_types.h:13:22: error: features.h: No such file or directory
/usr/include/asm-i386/page.h:4:20: error: unistd.h: No such file or directory
/usr/include/linux/signal.h:4:20: error: signal.h: No such file or directory
In file included from /usr/include/linux/module.h:9,
                 from hello.c:2:
/usr/include/linux/sched.h:77:22: error: sys/time.h: No such file or directory
In file included from hello.c:2:
/usr/include/linux/module.h:41: error: field ‘attr’ has incomplete type
/usr/include/linux/module.h:49: error: field ‘kobj’ has incomplete type


Im completely confused... Plsssssss help
Thanks in advance
Cheers

---

### Post by vishvesh on 2010-03-11
Hi,
   Did you fix this issue? Am facing similar issues too.

---

### Post by PmDematagoda on 2010-03-11
> **vishvesh said:**
> Hi,
   Did you fix this issue? Am facing similar issues too.

You could've asked this in a new thread instead of asking it in a 2 year old thread which the OP probably might not even read.

Thread closed.

---

