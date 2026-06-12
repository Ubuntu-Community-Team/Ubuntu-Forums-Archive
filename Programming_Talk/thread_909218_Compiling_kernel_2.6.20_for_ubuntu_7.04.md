---
title: "Compiling kernel 2.6.20 for ubuntu 7.04"
date: 2008-09-03
forum: Programming Talk
---

### Post by rajez79 on 2008-09-03
Hi,

I tried of compiling a kernel 2.6.2 for ubuntu 7.04. I followed the steps given below.

1)  $: make clean
2)  $: make 
3)  $: make modules
4)  $: make modules_install
5)  $: make install
6)  $: cd /boot

**7)  $: mkinitrd -o initrd.ing-2.6.20 2.6.20**

8)  $: vi /boot/grub/menu.lst
9)  $: update-grub
10) $: reboot

Upto steps 6 it is proper and when i tried of mkinitrd am getting the following error. I cant able to proceed further.

**root@rajesh-desktop:/boot#** mkinitrd -o initrd.img-2.6.20 2.6.20
/usr/sbin/mkinitrd: add_modules_dep_2_5: modprobe failed
FATAL: Could not load /lib/modules/2.6.20/modules.dep: No such file or directory
.
.
.
FATAL: Could not load /lib/modules/2.6.20/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.20/modules.dep: No such file or directory
WARNING: This failure MAY indicate that your kernel will not boot!
but it can also be triggered by needed modules being compiled into
the kernel.
root@rajesh-desktop:/boot#

I thought of writing some device drivers for USB and PCI after compiling my new kernel...  Please help me in solving this issue. 

-rajez-

---

### Post by eldragon on 2008-09-03
im quite sure you are not building the kernel image as you should...

i followed this guide in the past...instead of getting the kernel source from kernel.org, use the ones downloaded with apt-get.

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

### Post by Zugzwang on 2008-09-03
> **rajez79 said:**
> I thought of writing some device drivers for USB and PCI after compiling my new kernel...  Please help me in solving this issue. 


I might be wrong but since when do you have to build your own kernel in order to write device drivers (to be included as modules)? Doesn't installing the kernel header suffice?

---

### Post by rajez79 on 2008-09-03
This kernel is also downloaded using apt-get only... Am sure with the steps which i have seen in many websites.. But i have no knowledge of the errors.

-rajez-

---

### Post by rajez79 on 2008-09-03
yeah zugzwang...itz enough.

But am very mucn interested in working in a new kernel. so that it wont corrupt my working kernel.

If anybody knows temme whatz wrong with these steps....???

---

### Post by Zugzwang on 2008-09-03
How does it corrupt your working kernel? If you load your module using "insmod" it may hang. Well, in that case you reboot your system. Then the module isn't loaded again. Same holds for your custom kernel, so where's the difference?

So if you don't want to change the configuration to load your custom module on boot-up automatically,  there should be no problem.

---

### Post by rajez79 on 2008-09-03
Ok... accepted... temme to createa custom kernel... if i compile my program for the running kernel am getting a lot errors.

---

### Post by rajez79 on 2008-09-03
Leave device driver programming... whatz wrong with my initrd command...??? temme how can make a one...!

---

### Post by Zugzwang on 2008-09-03
> **rajez79 said:**
> Ok... accepted... temme to createa custom kernel... if i compile my program for the running kernel am getting a lot errors.

..as you wrote in [this]("http://ubuntuforums.org/showthread.php?t=907460") thread for which a solution has been given. Did you try compiling the minimal example as written [here]("http://ubuntuforums.org/showpost.php?p=4766255&postcount=5")?

With regards to your second post, why don't you follow the Ubuntu method of kernel compiling?: [https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")

Finally, please refrain from posting comments that will cause confusion (as done [here]("http://ubuntuforums.org/showpost.php?p=5717796&postcount=17") - There are no errors in the kernel, headers have been used incorrectly).  And would you mind not using slang abbreviations and taking care of grammar and spelling as this is an international community and this makes things harder to read (slang abbreviations are locally different).

---

### Post by rajez79 on 2008-09-03
If i use the command 

gcc -I/usr/src/linux-headers-2.6.20-15/include dd.c

am getting the following output...

/usr/src/linux-headers-2.6.20-15/include/linux/bitmap.h: In function ‘bitmap_weight’:
/usr/src/linux-headers-2.6.20-15/include/linux/bitmap.h:253: error: ‘BITS_PER_LONG’ undeclared (first use in this function)

/usr/src/linux-headers-2.6.20-15/include/linux/cpumask.h: In function ‘__cpus_or’:
/usr/src/linux-headers-2.6.20-15/include/linux/cpumask.h:135: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.20-15/include/linux/cpumask.h:135: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.20-15/include/linux/cpumask.h:135: error: ‘cpumask_t’ has no member named ‘bits’

/usr/src/linux-headers-2.6.20-15/include/linux/cpumask.h:311: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.20-15/include/linux/cpumask.h:311: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.20-15/include/linux/cpumask.h:311: error: ‘cpumask_t’ has no member named ‘bits’
/usr/src/linux-headers-2.6.20-15/include/linux/cpumask.h:311: error: ‘cpumask_t’ has no member named ‘bits’

/usr/src/linux-headers-2.6.20-15/include/linux/module.h:48: error: field ‘attr’ has incomplete type
/usr/src/linux-headers-2.6.20-15/include/linux/module.h:59: error: field ‘kobj’ has incomplete type

/usr/src/linux-headers-2.6.20-15/include/asm/system.h:346: error: expected declaration specifiers or ‘...’ before ‘u8’
/usr/src/linux-headers-2.6.20-15/include/asm/system.h:347: error: expected declaration specifiers or ‘...’ before ‘u16’
/usr/src/linux-headers-2.6.20-15/include/asm/system.h:347: error: expected declaration specifiers or ‘...’ before ‘u16’
/usr/src/linux-headers-2.6.20-15/include/asm/system.h:348: error: expected declaration specifiers or ‘...’ before ‘u32’
/usr/src/linux-headers-2.6.20-15/include/asm/system.h:348: error: expected declaration specifiers or ‘...’ before ‘u32’

/usr/src/linux-headers-2.6.20-15/include/linux/percpu.h:65: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.20-15/include/linux/percpu.h:71: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.20-15/include/linux/percpu.h:77: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘void’

/usr/src/linux-headers-2.6.20-15/include/asm/module.h:62:2: error: #error unknown processor family
In file included from dd.c:5:
/usr/src/linux-headers-2.6.20-15/include/linux/module.h:48: error: field ‘attr’ has incomplete type
/usr/src/linux-headers-2.6.20-15/include/linux/module.h:59: error: field ‘kobj’ has incomplete type

---

### Post by Zugzwang on 2008-09-03
See [this]("http://ubuntuforums.org/archive/index.php/t-559791.html") post. You need to provide some additional information about the kernel configuration. In my case I found them in "/lib/modules/2.6.22-14-generic/build/.config".

Again, using google would have helped in this situation. I got that page by searching for "linux/bitmap.h:253: error: ‘BITS_PER_LONG’ undeclared".

---

### Post by rajez79 on 2008-09-17
Hi,

If anybody is getting the same errors like me, then follow these steps.

1. write obj-m:=filename.c in a makefile.
2. goto prompt and type
   $ make -C /lib/modules/`uname -r`/modules SUBDIRS=`pwd` modules

NOTE : the uname -r and pwd are inside escape sequences (`) and not single quote(').

Mostly it wont give any errors and your code will get compiled properly.

---

