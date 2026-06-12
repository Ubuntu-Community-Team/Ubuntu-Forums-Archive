---
title: "win4lin kernel 2.6.10 for hoary"
date: 2005-03-02
forum: Programming Talk
---

### Post by toojays on 2005-03-02
```
When combining Ubuntu's kernel 2.6.10-24 with Win4Lin's
Kernel-Win4Lin3-2.6.10 patch, this patch is also required.

Without this patch, the build fails with
"arch/i386/kernel/acpi/wakeup.o: Bad value". This error is caused by
the value of GDT_ENTRIES being 32 in the vanilla kernel, but 512 in
the Win4Lin kernel.

By John Steele Scott <toojays@toojays.net>, March 2, 2005.

--- linux-source-2.6.10/arch/i386/kernel/acpi/wakeup.S~ 2005-02-25 15:44:00.000000000 +1030
+++ linux-source-2.6.10/arch/i386/kernel/acpi/wakeup.S  2005-03-02 18:14:27.872528152 +1030
@@ -181,14 +181,14 @@
        .code32
        ALIGN

-.org   0x800
+.org   0x1800
 wakeup_stack_begin:    # Stack grows down

-.org   0xff0           # Just below end of page
+.org   0x1ff0
 wakeup_stack:
 ENTRY(wakeup_end)

-.org   0x1000
+.org   0x2000

 wakeup_pmode_return:
        movw    $__KERNEL_DS, %ax

```

---

### Post by hazza96 on 2005-03-21
[QUOTE=toojays]When combining Ubuntu's kernel 2.6.10-24 with Win4Lin's
Kernel-Win4Lin3-2.6.10 patch, this patch is also required.[/QUOTE]
Could something like that be the cause of me getting a message "bad: scheduling while atomic" trying to install win4lin on a custom kernel with the win4lin patches on Warty?

---

### Post by toojays on 2005-03-21
Sorry, I don't know the answer to that one. :(

---

### Post by spookylukey on 2005-04-23
[QUOTE=toojays]```
When combining Ubuntu's kernel 2.6.10-24 with Win4Lin's
Kernel-Win4Lin3-2.6.10 patch, this patch is also required.

```[/QUOTE]

Cheers, works now! (Compiles at least, I'm about to reboot).

Luke

---

### Post by spookylukey on 2005-04-23
It worked, and I'm running Win4Lin now.  But when booting, I got this message:

ACPI: Wakeup code way too big, S3 disabled

I don't think this happened before, with the normal Ubuntu code.

As I'm not running a laptop/notebook, this doesn't bother me (ACPI is to do with power management, and the only thing I need it for is turning my monitor off, and that seems to work fine still).  But I thought I'd put this up for those who might care.

---

### Post by kiddyfurby on 2005-05-16
hi i m using hoary
where's the patch that you are mentioning?
is it just those lines in the quote?
how can i apply the patch?

thx in advance

---

### Post by spookylukey on 2005-05-18
You could just edit the lines in the file linux-source-2.6.10/arch/i386/kernel/acpi/wakeup.S directly - lines starting with a '-' in the patch are to be removed, lines starting with a '+' should be added.

Or you can download the patch as a file from here:
[http://lukeplant.me.uk/downloads/Kernel-Win4Lin3-2.6.10_extra_for_ubuntu.patch](http://lukeplant.me.uk/downloads/Kernel-Win4Lin3-2.6.10_extra_for_ubuntu.patch)

To apply the patch, cd to the directory containing your Ubuntu linux sources, and in the root of the linux source (e.g. in the linux-source-2.6.10/ dir), do:

patch -p1 < /path/to/patchfile

-p1 strips the first directory name out of the patch, as you don't want it
/path/to/patchfile is the actual path of the saved patch.

BTW, this step only makes sense as part of a process to build a kernel, as per:
[https://www.ubuntulinux.org/wiki/KernelCompileHowto](https://www.ubuntulinux.org/wiki/KernelCompileHowto)

I used the KernelHowto method.  In this case, you need do this after getting and unpacking the Ubuntu sources and before configuring the kernel (there is a Win4Lin kernel option you must set).

---

### Post by kiddyfurby on 2005-05-19
I have the Kernel compiled!!
unfortunately i am unable to do a offline installation for win4lin

---

### Post by Lunde on 2005-05-31
**Quick question...**

I managed to run win4lin pro [http://www.ubuntuforums.org/showthread.php?t=38360](http://www.ubuntuforums.org/showthread.php?t=38360) 
...but it's horrible, now I want to try out win4lin9x

I'm on Hoary, 2.6.10-5  (386), I can't find the the place to patch. I've tried to locate the file wakeup.S but it does'nt exist in my system

Any idea of what to do to apply the patch?

Thanx guys

---

### Post by mave on 2005-05-31
[QUOTE=kiddyfurby]I have the Kernel compiled!!
unfortunately i am unable to do a offline installation for win4lin[/QUOTE]

For now, I was able to compile it, but got a "kernel panic" while booting. Did your win4lin-kernel boot right?

Markus

---

### Post by kiddyfurby on 2005-06-03
[QUOTE=mave]For now, I was able to compile it, but got a "kernel panic" while booting. Did your win4lin-kernel boot right?

Markus[/QUOTE]
the kernel compiled and installed
booted into x, but not netwrok
I suppose I did something wrong...
that's why I said I need to do offline installation

---

