---
title: "Install Problems, dual boot with XP"
date: 2014-02-23
forum: New to Ubuntu
---

### Post by Greenpalmer on 2014-02-23
Hi - I've tried four times now to install Xubuntu 12.04 LTS using both DVD and USB drives and each time the install seems to complete successfully but when I restart I just get a prompt saying: grub >

Each time I have had to repair Windows XP Pro (FIXMBR and FIXBOOT) to be able to boot the computer.

I would really like to use Linux but don't know why it won't install. 

Any help or advice much appreciated.

---

### Post by Vladlenin5000 on 2014-02-23
Hi, welcome!

So you're trying a dual-boot? If so how are you managing the partitions -or- what option are you choosing during the Ubuntu installation?
Although there are many way to do it I'll just remark the easiest way, assuming you have a Windows OS already installed -and- no UEFI since you mentioned Windows XP:
1. In Windows use its own tools to shrink its partition leaving enough unallocated space for the other OS. *DO NOT create new partition(s) in there, not with Windows anyway.*
2. Boot the Ubuntu installer a and select the proper installation method - use the empty space - in the step where it asks where to install it.

Doing so the Ubuntu will be installed with the default set of partitions - / and swap - created in the previously unallocated space and the boot loader - GRUB - will be in the MBR. The computer should start and after POST show you the grub menu where you can select which OS to start.

---

### Post by Greenpalmer on 2014-02-23
Hi - thanks for the reply.

That is exactly what I did - I used Easeus Partition Master in XP to shrink my Windows partition and left 50gb of unallocated space, then booted up with the Xubuntu install which (without asking me) installed itself unto that space. But then just grub>.

---

### Post by monkeybrain20122 on 2014-02-23
Maybe you should try installing it with 'advanced' or 'manual' (whatever it is called)  option so you can make sure that the bootloader is actually installed.

---

### Post by mörgæs on 2014-02-23
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by squakie on 2014-02-23
Another thing for everyone to keep in mind:  before you use any tool to shrink a partition, be sure to run Windows defrag on the disk at least TWICE, and be sure you have good backups.  Without doing the defrags you have a higher chance of data loss.

---

### Post by mastablasta on 2014-02-24
boot repair tool is what you need to run. it seems you installed grub in the wrong place.

---

