---
title: "Can't install or boot from liveCD on new Dell Vostro 200"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by Pxtl on 2008-10-17
I just ordered and received a new Dell box, and wanted to install Ubuntu on it.  Ubuntu kicks me out to an "initramfs" console when I try to install or boot from LiveCD.    At the console, occaisionally exception messages pop up every second or two saying ata2.00: exception Emask 0x0 Sact 0x0 Serr 0x0 action 0x2 frozencmd... well, you get the idea.

I think it's having a problem with the hard disk.  The HDD follows the typical dell recovery-partition crap - 55mb of wierd stuff at the beginning and 10 gigs in a windows compatible partition.  Could that be tripping up the mounting?

Any ideas?

Thanks in advance.

---

### Post by philinux on 2008-10-17
I'd try the alternate text base installer cd.

Also when your livecd boots choose "check cd for defects".

---

### Post by Pxtl on 2008-10-17
Check CD for defects crashes the same while loading Linux, same as other processes.  From what I'm reading elsewhere, it's a SATA driver that blows up when it looks at my hardware, but that's a vague guess.  I'm currently fetching OpenSUSE to see if it's a universal problem.

Any other ideas?

---

### Post by gletob on 2008-10-17
I'm thinking really bad cd problem

---

### Post by Pxtl on 2008-10-17
Really?  Because doing some more research, it sounds similar to the bug in this monstrous thread:

[http://ubuntuforums.org/showthread.php?t=765195](http://ubuntuforums.org/showthread.php?t=765195)

Now, setting up irqpoll fixed the problem - it no longer crashes out to the busybox...

however, it doesn't work either.  Instead, it freezes up after ath_pci, on 
"ACPI: PCI Interrupt 0000:02:01[A] -> GSI 16 (level, low) IRQ 16"

Either way, I'm dling OpenSUSE, in hopes that works better.  I really would rather use Ubuntu though.

---

### Post by gali98 on 2008-10-17
If you are relatively computer literate, you may try the intrepid beta.
It has a lot of stuff fixed on these issues.
You may also try the boot options (It is one of the boot options when the cd first comes up.. f6 I think)
Try no aplc and other options.
Kory

---

### Post by eternalnewbee on 2008-10-17
> **Pxtl said:**
> Really?  Because doing some more research, it sounds similar to the bug in this monstrous thread:

[http://ubuntuforums.org/showthread.php?t=765195](http://ubuntuforums.org/showthread.php?t=765195)

Now, setting up irqpoll fixed the problem - it no longer crashes out to the busybox...

however, it doesn't work either.  Instead, it freezes up after ath_pci, on 
"ACPI: PCI Interrupt 0000:02:01[A] -> GSI 16 (level, low) IRQ 16"

Either way, I'm dling OpenSUSE, in hopes that works better.  I really would rather use Ubuntu though.

One problem I encountered in the past is that the cd was burned at too high speeds.

---

### Post by Pxtl on 2008-10-18
Nope.  Burned at lowest speed, problem persists.

edit: damn - same problems in Suse.

---

### Post by gali98 on 2008-10-18
There is a way to edit boot options on the cd. I don't know the specifics of it, but you should be able to edit the boot line.
Once you do that, scroll to the end and append:
noapic nolapic irqfixup

and see if that will let you boot up.
I also suggest trying the intrepid beta cd to see if it will boot up.
Kory

---

### Post by gmjs on 2008-10-18
I'm having exactly the same problem on a PC I've bought recently.

I purchased Vista Home Premium as I work in IT and need to know about it.  Now I know how much space it takes up (17GB for a clean install :lolflag:), I wanted to partition up and install Ubuntu alongside.

I'm using a known-good Live CD for installing Ubuntu 8.04.1 (installs to my old machine with no problems).

My PC has 4GB RAM and I'm installing the 32-bit version (I was just testing - I'm hoping to install the 64-bit version of 8.10 when it's out).

Would trying to install the 32-bit version with 4GB RAM be causing a problem?

Thanks,

Graham

---

### Post by gmjs on 2008-10-18
Ok, I've had a quick read and it seems that the current versions of Linux do not support SATA hard disk drives that use the IDE specification.

Windows Vista supports both IDE and AHCI specification SATA drives, and supports SATA Optical drives with the AHCI specification as of SP1.

Windows XP (to the best of my knowledge) does not support the AHCI spec.

If I'm right, that means you cannot dual boot Windows XP and Ubuntu with a SATA hard disk drive, which seems a bit strange.  I'd like to see Linux support for SATA drives without depending on AHCI.

Anyway - if your PC is to run only Ubuntu, check the BIOS for a HDD specification selection and change it to AHCI.

If you're running Vista and installed it with the IDE specification, enable the AHCI driver under Vista (see KB article [http://support.microsoft.com/kb/922976]("http://support.microsoft.com/kb/922976"), THEN make the switch.

I haven't tried it yet though.  I think I want a backup first!

Hope this helps.

---

### Post by gali98 on 2008-10-19
On the 4 gigs of ram, you will not have any trouble installing a 32bit OS, but the OS will only be able to use ~3.4 or so Gigs. That is the limitation of a 32bit OS.
Kory

---

### Post by Pxtl on 2008-10-20
Solved... sort of.

The problem was twofold.

First, there was the SATA problem, which was solved by booting with IRQPOLL in the options (for others stumbling into this thread, hit F6 to add text options and type in "IRQPOLL" into the command line options)

The second was that my DWL-520 Wireless board was killing things somehow.  I have no idea what the problem was, but I needed a new board anyways since this is a Vista dual-boot machine and the DWL-520 doesn't have Vista support, so I had to go out and buy myself a new wireless board.

Anybody else trying to get Ubuntu 8.04 on a Vostro 200 (they re-use that product name, so note that this is Fall 2008), irqpoll is the solution. (edit: gmjs, you should try that).

So, that's how this story ends.

---

### Post by gali98 on 2008-10-20
glad you got it worked out!
Kory

---

### Post by gmjs on 2008-10-24
Thanks Pxtl, I will!

---

