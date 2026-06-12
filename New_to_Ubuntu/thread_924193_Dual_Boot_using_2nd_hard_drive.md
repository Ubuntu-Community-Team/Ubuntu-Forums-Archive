---
title: "Dual Boot using 2nd hard drive"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by jdrob on 2008-09-19
I'm a new forum member and qualify as an absolute beginner.
My question is . . "is it possible to use a 2nd installed hard drive for Ubuntu and leave the first drive for XP?  

If so how does one go about this without wiping out the first drive?

Thanks,
jdrob

---

### Post by overdrank on 2008-09-19
> **jdrob said:**
> I'm a new forum member and qualify as an absolute beginner.
My question is . . "is it possible to use a 2nd installed hard drive for Ubuntu and leave the first drive for XP?  

If so how does one go about this without wiping out the first drive?

Thanks,
jdrob

Hi and welcome, here are some links that may help. Partitioning is the first 
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
And here is one for the dual boot installation
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Elfy on 2008-09-19
It certainly is - when you run the installer and get to the partition part - choose the second hard drive and tell it to use it.

It is likely, but not certain, that the second drive is shown as sdbx depending on how many partitions there are; linux numbers drives/partitions in a different way to windows.

As long as you tell it to install to the drive you want that is what it will do.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) is a good guide

---

### Post by aeiah on 2008-09-19
i use two different hard drives for mine. just make sure you install ubuntu and grub to the correct hard drive. when its all installed, make sure you go into your bios and select this hard drive to boot from by default (well actually, select it to boot from a cdrom first if available, then boot from the hard drive with ubuntu on it). grub will then allow you to select which operating system you want to boot. if your bios is set to boot off your windows hard drive, then it'll just boot windows and you wont have a choice.

if you cant figure out which hard drive is which, unplug one and go into your bios. the only hard drive detected will obviously be the one that's plugged in.

if you're really worried about wiping out windows you could install ubuntu with the windows hard drive unplugged, but this will mean that windows wont be automatically detected and added as a boot option in grub, so its best to leave it plugged in and just make sure you select the right hard drive.

---

### Post by Radioman991 on 2008-09-19
I used this to do mine


[http://ubuntuforums.org/showthread.php?t=179902&highlight=confused57](http://ubuntuforums.org/showthread.php?t=179902&highlight=confused57)

Worked great.  First time I tried to set things up, I killed my NTLDR on the XP drive.  To ensure I didn't do it again, I unplugged the power to the XP drive, and use GRUB to boot.  I can select either OS from GRUB.

Been using a year plus this way

Best,

Radioman991

---

