---
title: "finding my old OS on ubuntu"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by duquer on 2008-10-04
when installed ubuntu it did not let me choose between OS with vista and ubuntu it automatically runs Ubuntu when the computer is turned on.i tried activating lilo but it wont let me do it through the terminal...how do i find the directory and configure my system to get give me a choice of which OS i want to run. im kind of a beginner at this so if you can explain it fully it will be well appreciated. im pretty sure i didnt delete vista i just cant find it and i dont know where to begin. thank you

---

### Post by RequinB4 on 2008-10-04
Assuming when you installed you didn't overwrite your old OS by using the entire disk, when you boot at some point you should see white text with a few seconds countdown - this is GRUB - press escape, and choose your operating system (might be on the bottom) with the keyboard.

---

### Post by mikewhatever on 2008-10-04
Please open Applications->Accessories->Terminal and post the output of the following:
sudo fdisk -l

---

### Post by Sef on 2008-10-04
> Please open Applications->Accessories->Terminal and post the output of the following:
sudo fdisk -l

That will show what partitions you have on your hard disk.  If you dual booted both operating systems will be shown.  If not, then only Ubuntu will be shown.

---

### Post by crapple on 2008-10-04
If you had you still have vista installed I think if you type help in yaboot. It will give you an option to type in to boot vista.

---

### Post by kansasnoob on 2008-10-04
> **duquer said:**
> when installed ubuntu it did not let me choose between OS with vista and ubuntu it automatically runs Ubuntu when the computer is turned on.i tried activating lilo but it wont let me do it through the terminal...how do i find the directory and configure my system to get give me a choice of which OS i want to run. im kind of a beginner at this so if you can explain it fully it will be well appreciated. im pretty sure i didnt delete vista i just cant find it and i dont know where to begin. thank you


Ubuntu does not use Lilo unless you specifically installed Lilo as your bootloader. Neither does Vista.

Can you even boot Ubuntu?

---

### Post by 3rdalbum on 2008-10-04
> **crapple said:**
> If you had you still have vista installed I think if you type help in yaboot. It will give you an option to type in to boot vista.

Yaboot is for PowerPC-based machines only.

When Ubuntu installs, it almost always detects Windows and adds it to the boot menu. If it doesn't appear on the boot menu, there's the possibility that either something has gone wrong at the partitioning step, or that you've erased Windows.

Please post the output of this command so we can confirm if you have indeed erased Windows:

```
sudo fdisk -l
```

Thanks.

---

### Post by duquer on 2008-10-05
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       76737   616389921   83  Linux
/dev/sda2           76738       77825     8739360    5  Extended
/dev/sda5           76738       77825     8739328+  82  Linux swap / Solaris

---

### Post by tangibleorange on 2008-10-05
> **duquer said:**
> Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       76737   616389921   83  Linux
/dev/sda2           76738       77825     8739360    5  Extended
/dev/sda5           76738       77825     8739328+  82  Linux swap / Solaris

oh dear... i'm afraid your windows is gone...

---

### Post by duquer on 2008-10-05
when i first installed Ubuntu in the rhythmbox music player it pulled up songs that i use to have in itunes  but after a while they disappeared. so i was thinking vista was still in there somewhere i just got to find it and set it up to were  it is a dual boot

---

### Post by kansasnoob on 2008-10-05
> **duquer said:**
> Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       76737   616389921   83  Linux
/dev/sda2           76738       77825     8739360    5  Extended
/dev/sda5           76738       77825     8739328+  82  Linux swap / Solaris

It's gone! You have a Linux partition and a swap partition (contained in an extended partition). You wiped windows out!

---

