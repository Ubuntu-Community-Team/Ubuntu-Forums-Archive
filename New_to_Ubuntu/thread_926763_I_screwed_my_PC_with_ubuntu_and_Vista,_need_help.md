---
title: "I screwed my PC with ubuntu and Vista, need help"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by Kladionica on 2008-09-22
Recently i've tried to install ubuntu 8.04 inside windows several times but i was continuously getting this error at boot:

```
Try (hd0,0):NTFS5:2
Try (hd0,1):invalid or null
Try (hd0,2):invalid or null
Try (hd0,3):invalid or null
(fd0)FAT12:no WUBIDLR

ERROR:Cannot fing GRLDR in all devices.
```

Then i lookup in google to find solution in some forums,and i guess i misinterpreted something and i downloaded grub4dos and the 3-4 files in there (i think Menu.ist ,grldr.mbr,grldr don't remember that much),i putted in the Ubuntu folder in local disk C (C\ubuntu\disks\boot\grub and C\\ubuntu\winboot).
After booting i didn't get the dualboot with vista and ubuntu anymore,but instead i got the grub4dos menu which was useless,and i couldn't get through it to the bootloader of vista or ubuntu.To make things worse through the LiveCD i managed to get into the local disc and i deleted](*,) the grub4dos files in the ubuntu folder and now i still get the grub4dos bootloader but just with a command prompt :```
grub> 
```.

Can anyone help me with this?

---

### Post by clancymf on 2008-09-22
Have you tried your windows recovery disk.

I would try that and then it should update the bootloader.

When installing Ubuntu, you need to install it on a seperate partition, not within windows.

---

### Post by Kladionica on 2008-09-22
> **clancymf said:**
> Have you tried your XP recovery disk.

I would try that and then it should update the bootloader.

When installing Ubuntu, you need to install it on a seperate partition, not within windows.
I've tried and i couldn't upgrade (the option was not available)and i also tried system restore and the other tools and it's still the same.I've installed Ubuntu 8.04 with wubi and it's installed on windows

---

### Post by billgoldberg on 2008-09-22
> **clancymf said:**
> Have you tried your windows recovery disk.

I would try that and then it should update the bootloader.

When installing Ubuntu, you need to install it on a seperate partition, not within windows.

He was talking about Wubi.

Wubi isn't consider 100% stable. And you won't get a good performance compared to a real install.

Create a separate partition on your HDD and install Ubuntu that way.
*(google for "dual boot ubuntu vista" should bring up some guides)*

Or use something like Virtual Box to start Ubuntu after you have booted into Windows (I think you won't be able to use 3d effects then, not sure).

---

### Post by billgoldberg on 2008-09-22
> **Kladionica said:**
> I've tried and i couldn't upgrade (the option was not available)and i also tried system restore and the other tools and it's still the same.I've installed Ubuntu 8.04 with wubi and it's installed on windows


Download the "Super Grub Disk" live cd.

Burn it to cd as an image (like you did Ubuntu). 

Boot from it. 

The interface is pretty easy to use, you should be within Vista in seconds. 

I believe it can also repair the mbr.

---

### Post by Kladionica on 2008-09-22
> **billgoldberg said:**
> Download the "Super Grub Disk" live cd.

Burn it to cd as an image (like you did Ubuntu). 

Boot from it. 

The interface is pretty easy to use, you should be within Vista in seconds. 

I believe it can also repair the mbr.
it would be great if i could burn it ,because i have only one dvd writer which got the LiveCD inside that i'm using now

---

### Post by cmat on 2008-09-22
You can dual boot. But if things get to dicey you can recover your Windows partition in a just a few simple steps given you have an installation disc.

Place your installation media in the drive, wait until it loads then select "repair your computer". Your Vista partition should appear on a list. Select it then click "system recovery options" then "command prompt". Here you can recover your MBR with a few commands. 

Type the following into the console:

This will "repair" the MBR with Microsoft's bootloader. 

```
bootrec /FixMbr
```

Then...

```
bootrec /FixBoot
```

This should add Vista to the boot loader you created in the previous step.

This should fix it once and for all. Now that you have your partition bootable. I recommend you to partition your hard-drive and then install Ubuntu on it's own dedicated partition. 

If you have a recovery disk from a vendor. You will need to follow the on screen instruction when you boot it up to recover your drive. Some vendors supply a recovery console on the DVD others don't.

---

### Post by kansasnoob on 2008-09-22
I'm not sure if this will help you or not, but if you need to restore Vista's mbr and/or boot look at my post #4 here:

[http://ubuntuforums.org/showthread.php?t=926764](http://ubuntuforums.org/showthread.php?t=926764)

---

