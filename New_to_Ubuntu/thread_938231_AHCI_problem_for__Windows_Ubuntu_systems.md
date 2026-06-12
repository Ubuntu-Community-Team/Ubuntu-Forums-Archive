---
title: "AHCI problem for  Windows/ Ubuntu systems"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by Unewbeginner on 2008-10-04
Hello, I have one Windows XP on my hard drive and I installed 64bit Ubuntu 8.04 on the same hard drive.

At first ubuntu installation didn't go through and I only got some prompts called "initramfs".

Then I read some posts and found that it may work if i change the option of AHCI at BIOS.

So I went to BIOS --> Integrated Peripherals --> SATA AHCI Mode, and saw two options: AHCI or Disabled. I changed it to AHCI and tried to install ubuntu again, and it works.

But when I boot again, I can't get in my windows unless I change the option back to "Disabled" at BIOS. But under this option, I can't get in Ubuntu......

Sorry for the complicated description, but could anyone here help me on this issue? I just want to make my both systems work well.

Thanks,

---

### Post by Unewbeginner on 2008-10-05
anybody...

---

### Post by cariboo on 2008-10-05
WHat version of Windows XP are you using, becuse anything past sp2 should detect SATA drives natively instead of using emulation.

JIm

---

### Post by Therion on 2008-10-05
> **cariboo907 said:**
> WHat version of Windows XP are you using, becuse anything past sp2 should detect SATA drives natively instead of using emulation.

JIm
Funny word "should".

I say that because I'd been going round and round with a related issue myself and a SATA slave.  I got to choose if I wanted to use it Ubuntu or in WinXP (I was dual-booting at the time) and then I had to set the BIOS' AHCI setting accordingly because no amount of fiddling would get it recognized in both OS'es.  I never was able to find a work around for this issue.  It was weird because my XP install CD is slipstreamed with additional drivers and SP3 on top of it and my primary drive is SATA as well (WD Raptor).  Go figure.  At some point I just gave up trying.

Then I dumped Windows (again).  Now everything is fine.

---

### Post by Unewbeginner on 2008-10-05
Hello Jim, I'm using Windows XP professional SP3.

The trouble I have right now is that I can only install my Ubuntu with AHCI enabled. But on the other hand, I can only install my Windows with AHCI disabled.

I tried to enable the AHCI after I installed my Windows (with some guide I found online), but I can't make it work.

> **cariboo907 said:**
> WHat version of Windows XP are you using, becuse anything past sp2 should detect SATA drives natively instead of using emulation.

JIm

---

### Post by Paqman on 2008-10-05
> **Unewbeginner said:**
> 
I tried to enable the AHCI after I installed my Windows (with some guide I found online), but I can't make it work.

Do you have the disks for your motherboard? If not, go to the manufacturer's website. They should have a driver available that will let Windows talk to one of these new-fangled SATA devices.

---

### Post by Unewbeginner on 2008-10-05
> **Therion said:**
>  I got to choose if I wanted to use it Ubuntu or in WinXP (I was dual-booting at the time) and then I had to set the BIOS' AHCI setting accordingly because no amount of fiddling would get it recognized in both OS'es.  I never was able to find a work around for this issue.  It was weird because my XP install CD is slipstreamed with additional drivers and SP3 on top of it and my primary drive is SATA as well (WD Raptor).  Go figure.  At some point I just gave up trying.

Hello Therion, is it really impossible to make it work...? If so, could anyone here let me know why I can't install my Ubuntu 8.04 with AHCI disabled?

Thanks,

---

### Post by Therion on 2008-10-05
> **Unewbeginner said:**
> Hello Therion, is it really impossible to make it work...? If so, could anyone here let me know why I can't install my Ubuntu 8.04 with AHCI disabled?

Thanks,
I don't want to say it's not *possible* to do it, but I couldn't find an answer.  
Sorry, but I'm at a loss as to explain why it's such a pain; that's way over my head.

---

### Post by Unewbeginner on 2008-10-05
Yes I have the disk on my hand. Could you explain how to make it work with the disk?

Thanks,

> **Paqman said:**
> Do you have the disks for your motherboard? If not, go to the manufacturer's website. They should have a driver available that will let Windows talk to one of these new-fangled SATA devices.

---

### Post by Paqman on 2008-10-05
> **Unewbeginner said:**
> Yes I have the disk on my hand. Could you explain how to make it work with the disk?


Disable AHCI so that you can boot into WIndows, then pop the disk in and see if it will let you install the SATA drivers. It'll probably be called a "storage controller" or some such. If in doubt, reinstall all the drivers for the chipset.

---

