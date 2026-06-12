---
title: "Problem: Installing Dual-Booting with Windows XP"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by KeithA45 on 2008-09-02
Hey guys,

I just installed Ubuntu on my Compaq Presario SR1230NX and followed the instructions to dual-boot it, except since I wanted to partition room for another OS (PCLinux OS), I manually partitioned the disk using GParted, and when the time came to install, I made sure that the remaining windows partition was set to NTFS, and I made sure NOT to format it.

Unfortunately, now when I try to boot to windows, I get:

"A disk read error occurred
Press Ctrl+Alt+Del to restart"

...every time.

I backed up the data so I can install XP on there again and what-not if I have to, but I'd like to fix it if at all possible.

Help?

Thanks,
 - Keith

---

### Post by aimpau on 2008-09-02
Hi there,

visit this [thread]("http://ubuntuforums.org/showthread.php?t=179902"). I also dual boot with XP and this thread helped a lot.

Enjoy!

---

### Post by Tatty on 2008-09-02
Can you boot into ubuntu fine?

If so, can you post the output of

```
sudo fdisk -l
```

note: thats a lowercase L

---

### Post by KeithA45 on 2008-09-03
> **Tatty said:**
> Can you boot into ubuntu fine?

If so, can you post the output of

```
sudo fdisk -l
```

note: thats a lowercase L

Sure:


keith@Desktop-Ubuntu:~$ sudo fdisk -l
[sudo] password for keith: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4c8e4c8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30819   247553586    7  HPFS/NTFS
/dev/sda2           30820       34735    31455270   83  Linux
/dev/sda3           34736       38651    31455270   83  Linux
/dev/sda4           38652       38913     2104515   82  Linux swap / Solaris


Thanks in advance for the help

---

### Post by Tatty on 2008-09-03
Well your windows partition is definately still there, so you dont need to worry about having overwritten it.

However, the error message you are getting is worrying, it sounds like windows has gotten corrupted somehow.  It could be either a hardware problem, or an unlucky copying error when repartitioning the drive.

I have tried googling the error message but no particularly helpful pages are jumping out at me.  It may be worth booting into the windows install CD and trying their repair / recovery options.  This might cause windows to overwrite the MBR with its own, preventing you from booting into ubuntu, although this can easily be fixed afterwards by following these instructions...[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Sorry I cant be more helpful, but this appears to be a windows problem and I am no windows expert ;)

---

### Post by KeithA45 on 2008-09-03
> **Tatty said:**
> Well your windows partition is definately still there, so you dont need to worry about having overwritten it.

However, the error message you are getting is worrying, it sounds like windows has gotten corrupted somehow.  It could be either a hardware problem, or an unlucky copying error when repartitioning the drive.

I have tried googling the error message but no particularly helpful pages are jumping out at me.  It may be worth booting into the windows install CD and trying their repair / recovery options.  This might cause windows to overwrite the MBR with its own, preventing you from booting into ubuntu, although this can easily be fixed afterwards by following these instructions...[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Sorry I cant be more helpful, but this appears to be a windows problem and I am no windows expert ;)

Naw when I put in the XP disk, it didn't even give me the option to repair, just standard new installation, which isn't a big deal.

Thanks for your help, and I'm probably going to need that link you provided =)

---

### Post by Tatty on 2008-09-03
> **KeithA45 said:**
> Naw when I put in the XP disk, it didn't even give me the option to repair, just standard new installation, which isn't a big deal.

Thanks for your help, and I'm probably going to need that link you provided =)

Im sure there is a repair option in there somewhere... I have used it before, but unforunately i cant remember the exact process to get to it.

---

### Post by caljohnsmith on 2008-09-03
I've seen this type of error before with Windows after setting up a dual-boot, and I think the chances are high you can repair it without too much trouble. The first step would be to boot your Windows Install CD, and run "fixboot", which will repair the boot sector of the Windows partition. Also, we need to confirm Grub is trying to boot Windows correctly, so please post the output of:
```
cat /boot/grub/menu.lst
```
Also, did you defragment your Windows partition before resizing it?

---

