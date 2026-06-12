---
title: "New to ubuntu"
date: 2020-09-23
forum: New to Ubuntu
---

### Post by patchin on 2020-09-23
Ubuntu start up
I just got a dell xps 13 9370 laptop.i turn it on and I get the ubuntu logo and then it goes to a command prompt.How do I proceed from here.

---

### Post by TheFu on 2020-09-23
What did you expect to happen?

If you want a GUI, try running **startx**.
On Unix-like OSes, a GUI is optional.  Normally, someone would install a desktop version on a laptop, but who knows what you got or requested?  

If it were me, I'd assume the system was corrupted and create a boot/installation flash drive, boot off that, then do a fresh install of the specific Ubuntu flavor that I prefer to have. Installation takes about 12 minutes, last time I checked.  There are a few different options for DEs.  Changing between the different Desktop Environments isn't too hard. Takes about 3-5 minutes.  A DE is just another program, it isn't tied into the OS like it is on Windows.  We have have lots of different DEs installed on the same machine, though it is best to use a different userid/login with each to avoid user configuration conflicts.

The laptop you have can have either a Core i5 or i7 CPU.  I have a laptop with the i5-8250u and installed Ubuntu Mate on it before I decided to use a different GUI. I wanted something lighter, but any DE would run reasonably well on the box, so you have about 10 choices.

---

### Post by oldfred on 2020-09-23
Dell typically needs UEFI update, if SSD also SSD firmware update.
It needs UEFI setting for drives changed to AHCI, not Intel RST nor RAID. But if dual booting with Windows you must first install AHCI drivers into Windows or it will not boot.
Often better to have UEFI Secure boot off. And UEFI fast boot off, as that assumes no system changes & you are changing system.
Older Dell seemed to need legacy on, but still select UEFI to boot (without secure boot). Newer systems need legacy off to boot in UEFI mode.
And in Windows you need Windows fast start up off as that sets hibernation flag and then Linux NTFS driver cannot see the NTFS partitions. Note that Windows updates may turn fast start up back on.
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)
Dell - All
[https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup](https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup)
How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

Dell XPS13 9370 Developer Edition - Install Windows after Ubuntu
[https://askubuntu.com/questions/1203329/installing-windows-10-dual-boot-after-installing-ubuntu-on-a-custom-ubuntu-comp](https://askubuntu.com/questions/1203329/installing-windows-10-dual-boot-after-installing-ubuntu-on-a-custom-ubuntu-comp)
Dell XPS 13 9370 Kabylake Makes For A Great Linux Laptop comparison to older laptops
[https://www.phoronix.com/scan.php?page=article&item=dell-xps13-9370&num=1](https://www.phoronix.com/scan.php?page=article&item=dell-xps13-9370&num=1)

---

### Post by patchin on 2020-09-23
Thanks for your reply.'startx' didn't do anything. If you have other commands I could enter can you please post them.

---

### Post by TheFu on 2020-09-23
> **patchin said:**
> Thanks for your reply.'startx' didn't do anything. If you have other commands I could enter can you please post them.

That's the normal command to start a GUI, but seriously, **I'd just do a fresh install.** Be certain to look over Oldfred's links. I don't have an XPS, though I have used a few Dell laptops for Linux and found them to be really compatible over the decades.  

With Linux, having a bootable install/Try Ubuntu flash drive is handle for all sorts of reasons, including the ability to fix some things. Assign an 8G flash drive just for that purpose.  Refresh the ISO on it every quarter or 6 months.

---

### Post by patchin on 2020-09-23
Thanks again for your time

---

### Post by QIII on 2020-09-23
By chance, did you install a minimal image or the server image?

---

### Post by patchin on 2020-09-23
I didn't install anything

---

### Post by TheFu on 2020-09-23
> **patchin said:**
> I didn't install anything

What, exactly, does the screen look like?  Do you get to login?  Does it say "GRUB" or "Grub Rescue"?  Or something else?

---

### Post by patchin on 2020-09-23
It says (initramfs)

---

### Post by TheFu on 2020-09-23
> **patchin said:**
> It says (initramfs)

You aren't in Ubuntu.  There's a boot failure.  At this point, just reinstall, wipe the OS completely.  There isn't any easy fix we can talk you through as a beginner.  Whereas an install should be 12 minutes.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

There are instructions for Windows, OSX, and Linux systems. If all you have is this machine, you'll need a friend's machine to make an install flash drive.  A 4G flash drive should be enough. It will be completely wiped.  USB, SDHC whatever slots your laptop has should work. I often boot my laptops from an SDHC slot to try new releases out. USB2 or USB3 flash can work too.  If USB3 doesn't work, try the USB2 port on the machine. It will be a little slower, but that really doesn't matter for emergency needs like this.

---

### Post by ajgreeny on 2020-09-24
It sounds as if you bought the Dell with Ubuntu already installed and if this is the case and you have not yet managed to start Ubuntu you should go back to the seller and get them to fix it.

---

### Post by oldfred on 2020-09-24
If preinstalled Ubuntu, systems usually have a recovery method.
With Ubuntu it often is then a copy of the ISO that you can boot from grub.

If you press f12 to you get a UEFI boot menu.
Or press escape during Dell logo and get a grub boot menu?

---

### Post by patchin on 2020-09-24
That's the best advice I got thanks

---

### Post by ajgreeny on 2020-09-24
> **patchin said:**
> That's the best advice I got thanks
What was?

It will help others to  know which suggestion worked.

---

### Post by patchin on 2020-09-24
Getting on to the seller

---

### Post by patchin on 2020-09-25
> **ajgreeny said:**
> What was?

It will help others to  know which suggestion worked.

Problem was indeed in the BIOS settings.

System Configuration --> SATA Operation Changed RAID to AHCI.

Bingo.

---

### Post by ajgreeny on 2020-09-26
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by aaronrv2008 on 2020-09-27
That means something got messed up in while installation. Obtain another copy of Ubuntu from the website ( [https://ubuntu.com/download](https://ubuntu.com/download) ) and select "Ubuntu Desktop". Then install it onto the system.

---

### Post by NM5TF on 2020-09-27
in post #17 he says it's now fixed by a change in BIOS settings....

---

### Post by math492m on 2020-09-28
cant you just install a fresh copy off ubuntu desktop(GUI) if you dont want it to be just terminal

---

