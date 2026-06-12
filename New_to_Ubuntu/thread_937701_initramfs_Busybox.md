---
title: "initramfs? Busybox?"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by Unewbeginner on 2008-10-04
Hi all, I'm installing 64bit Ubuntu 8.04 and got some troubles. After the Ubuntu logo flash, I got the message below:

busybox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)

I once installed 64bit ubuntu8.04 two months ago but I never got this message and all the installation just took me less than 1 hour. This time I just change my motherboard and I got this trouble.

I have one Windows XP on my harddrive and I'm trying to have Ubuntu as my second OS. Please help me getting rid of this problem.

Thanks,

---

### Post by Orange_and_Green on 2008-10-04
Hi :)

Sounds like hardware failure/incompatibility or missing drivers. When you boot the install CD, try pressing F6 ("other options") and add this to the text you see:
```
acpi=off
```

Does it get any better?

If that fails, you might want to go into BIOS and have a look at the disk drive settings. If you have SATA disks and they are set on AHCI, you might want to set them to "legacy" or IDE emulation and see what happens.
*NOTE: if you installed Windows with AHCI and you want to boot back to windows, you might have to set the option back to ahci. However, I still recommend you try this out because  if the live cd manages to boot with ahci disabled but not when it's enabled, then we have found the problem's cause. In that case, you might want to see if the motherboard's vendor supplies any linux drivers for the SATA controller. Or, if you do not need ahci, keep it disabled and repair the windows installation so it boots without ahci.*
What model is your new motherboard?

Keep us posted, good luck:KS

---

### Post by Unewbeginner on 2008-10-04
Hi, I tried the code but it didn't work:(

I checked my BIOS and "SATA AHCI Mode" is disabled already.

My motherboard is Gigabyte EP43.

Hope someone could help me out.



> **Orange_and_Green said:**
> Hi :)

Sounds like hardware failure/incompatibility or missing drivers. When you boot the install CD, try pressing F6 ("other options") and add this to the text you see:
```
acpi=off
```

Does it get any better?

If that fails, you might want to go into BIOS and have a look at the disk drive settings. If you have SATA disks and they are set on AHCI, you might want to set them to "legacy" or IDE emulation and see what happens.
*NOTE: if you installed Windows with AHCI and you want to boot back to windows, you might have to set the option back to ahci. However, I still recommend you try this out because  if the live cd manages to boot with ahci disabled but not when it's enabled, then we have found the problem's cause. In that case, you might want to see if the motherboard's vendor supplies any linux drivers for the SATA controller. Or, if you do not need ahci, keep it disabled and repair the windows installation so it boots without ahci.*
What model is your new motherboard?

Keep us posted, good luck:KS

---

### Post by Unewbeginner on 2008-10-04
hello, anyone here could help me out?

Thanks

---

### Post by jmszr on 2008-10-04
Are you doing a full install or installing Wubi?

---

### Post by Unewbeginner on 2008-10-04
> **jmszr said:**
> Are you doing a full install or installing Wubi?

full installation.

---

### Post by neur0 on 2008-10-05
I have an P45 Gigabyte MB and Ubuntu can't see my hard drive at all. Turning SATA mode to either RAID or AHCI solves the problem but if you already have a Windows installation it may mess it up. You can fix it with switching back to IDE (disabled) and installing the correct chipset drivers.

---

### Post by felixdentro on 2009-05-13
I have exactly the same problem as Unewbeginner when tried to install ubuntu 8.04 64 bits as second OS in my PC: Intel Core 2 Quad Q9400, motherboard Gigabyte GA-EP43-DS3L, with a running Windows XP pro 32 bits. Tried to change SATA mode to AHCI according to neur0 advice, this worked with Ubuntu 8.04 but my WXP didn't run. I was unable to find the drivers for WXP to change to AHCI due to incompatibility of this mode with the southbridge in the chipset Eaglelake P43.
Solution: Tried Ubuntu 9.04 64 bits whit the SATA AHCI mode disabled, it installs and works perfectly and my WXP pro 32 bits is still happy in its corner of the harddrive.

Thanks to Unewbeginner, orange_and_green, and neur0 for your valuable help ):P.
Felix

---

### Post by thegreenkid on 2012-06-09
> **Orange_and_Green said:**
> Hi :)

Sounds like hardware failure/incompatibility or missing drivers. When you boot the install CD, try pressing F6 ("other options") and add this to the text you see:
```
acpi=off
```Does it get any better?

If that fails, you might want to go into BIOS and have a look at the disk drive settings. If you have SATA disks and they are set on AHCI, you might want to set them to "legacy" or IDE emulation and see what happens.
*NOTE: if you installed Windows with AHCI and you want to boot back to windows, you might have to set the option back to ahci. However, I still recommend you try this out because  if the live cd manages to boot with ahci disabled but not when it's enabled, then we have found the problem's cause. In that case, you might want to see if the motherboard's vendor supplies any linux drivers for the SATA controller. Or, if you do not need ahci, keep it disabled and repair the windows installation so it boots without ahci.*
What model is your new motherboard?

Keep us posted, good luck:KS


ahem ahem!!! a simple correction.... just enable ahci mode and it will start working... it did forr us...

---

### Post by oldos2er on 2012-06-09
Please don't bump old threads.

---

