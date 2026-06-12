---
title: "How to make kernel panic"
date: 2010-04-10
forum: Programming Talk
---

### Post by MrStill on 2010-04-10
Hi,

I know that this is a strange request; but, I am looking to write some C code that causes kernel panic. I have been looking at some of the **panic()** man pages and I have derived two non-working solutions both similar to:

```

#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
#include <tcl.h>
int main(){
	panic("Test");
	return 0;
}

```

The other is using the **panic()** function in **sys/systm.h**. The issue I am having in both cases is that **tcl.h** or **sys/systm.h** cannot be found.

```

joseph@joseph-touch:~$ gcc KernelPanic.c
KernelPanic.c:4:17: error: tcl.h: No such file or directory

```

Does anyone have any advise on how I could get this working?

Thanks
Joseph

---

### Post by johnl on 2010-04-11
Hi,

Not just any program running on the system can cause the kernel to panic.  In fact, I'm pretty sure a panic can only come from inside the kernel itself.  So you would need to build a kernel module or patch the actual kernel source in order to trigger a panic.

Building a kernel module will for sure be easier.  Find an example for this (I'm sure there are a few on this forum or on google -- [this one](http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html) looks promising), and then simply call panic from your module initialization function.

You can then case the panic by loading your kernel module with "insmod <yourmod.ko>" or "modprobe <yourmod.ko>" as root.

Hope this helps.

---

### Post by nvteighen on 2010-04-11
Wait, why do you need tcl.h? IIRC and from what I've googled, That's a header related to the Tcl programming environment's API... Maybe you were looking for linux/sysctl.h?

Second, I'm not quite sure whether panic() is designed for user-land usage... All I find is that it's designed as something internal to the kernel, maybe accessable for kernel modules, biut not for applications for sure. You know, having an application being able to stop the kernel anytime is not what I'd call a sane design...

---

### Post by km0r3 on 2010-04-11
Useful resources:

[http://linux-india.openscroll.org/linux-india-help/200003/msg00097.html](http://linux-india.openscroll.org/linux-india-help/200003/msg00097.html)
[http://www.faqs.org/docs/Linux-HOWTO/Linux-Crash-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Linux-Crash-HOWTO.html)  <-- This one is great.

---

### Post by uljanow on 2010-04-11
You could mess around with /sys and /dev directories.

dd if=/dev/zero of=/dev/mem bs=1M count=16
should have some interesting effects.

---

### Post by MrStill on 2010-04-23
> **johnl said:**
> 
[this one](http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html) looks promising

I used this tutorial and called panic() from the init function. It worked fine.

Thanks

---

