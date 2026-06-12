---
title: "Error messages when compiling a kernel"
date: 2007-01-01
forum: Programming Talk
---

### Post by woland on 2007-01-01
I'm trying to compile a kernel for uClinux. Since their support forum reminds me of a desert, I wanted to try my luck here.
This is the message that I get:
```
make[3]: Entering directory `/root/uClinux-dist-intec-2.4/linux-2.4.x/arch/m68knommu/kernel'
/root/uClinux-dist-intec-2.4/linux-2.4.x/scripts/mkdep -fno-builtin -nostdinc -D__KERNEL__ -I/root/uClinux-dist-intec-2.4/linux-2.4.x/include  -Wall -Wstrict-prototypes -Wno-trigraphs -O1 -g -fno-strict-aliasing -fno-common -I/include -pipe -DNO_MM -DNO_FPU -m5307 -Wa,-S -Wa,-m5307 -D__ELF__ -DMAGIC_ROM_PTR -DUTS_SYSNAME=\"uClinux\" -D__linux__ -O1  -nostdinc -iwithprefix include -- bios32.c console.c m68k_defs.c m68k_ksyms.c process.c ptrace.c semaphore.c setup.c sys_m68k.c time.c traps.c > .depend
realpath(/include) failed, No such file or directory

```
What could cause it and how do I fix it?
I know that this kind of error message is not bind only for uClinux.

---

### Post by kidders on 2007-01-01
Hi there,

[COLOR="Silver"]What version of Linux are your compiling the kernel on? An easy solution might be to symlink /include to something ... the question is what hehe.[/COLOR] (Stupid suggestion, sorry ... do what duff says!)

---

### Post by woland on 2007-01-01
I'm trying to compile linux kernel 2.4, WildFire for ColdFire microcontorller.

I'm trying to do that on Fedora Core 6, that I'm stuck with.
The FC is running 2.6.18-1.2798.fc6xen.

---

### Post by duff on 2007-01-01
looks like you're missing **realpath**, just install it and try again.

---

### Post by woland on 2007-01-02
There is no **realpath** binary on my system.
I've looked for a package that would contain it in numerous places, but couldn't find one.

---

### Post by kidders on 2007-01-02
Looks like util-linux is the package you're after.

---

### Post by woland on 2007-01-02
Thanks, but too bad that I need it for FC6...
Like I said, I'm stuck with Fedora.

Perhaps I can use alien to convert it?

BTW I did post this on Fedora forum, but still waiting for any answer.

---

### Post by woland on 2007-01-02
Used Debian version in FC. 

It wasn't the problem. Actually there was their own version of **realpath**. The error that it returns is that the **realpath** cannot find the location specified for it.

So the problem is elsewhere.

BTW, thanks to everyone who gave up from his/her time to answer this thread.

---

