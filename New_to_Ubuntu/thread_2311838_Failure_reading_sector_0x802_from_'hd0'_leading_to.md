---
title: "Failure reading sector 0x802 from 'hd0' leading to grub rescue....."
date: 2016-01-30
forum: New to Ubuntu
---

### Post by Edward_Marquardt on 2016-01-30
I'm fairly new to Ubuntu (3months) and linux base systems in general.  I switched due to Ubuntu (14.04.03 LTS) after replacing the original hard drive in a older laptop (Dell Inspiron N7010).  My harddrive is not partitioned (/dev/sda).

The only problem up until now was that the desktop manager acted up a month back which led me to loading gdm instead of lightdm.

A few days ago my wife was burning a cd using Brasero when the laptop locked up and would not respond.  She did a hard shut down and upon reboot got the following error before Ubuntu would load:

> error:Failure reading sector 0x802 from 'hd0'
Entering rescue mode...
grub rescue>

I booted up with the original copy of Ubuntu on USB.  

Ran checkdisk from the terminal:

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda
fsck from util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>
```

I attempted to load a backup superblock but the same message as above keeps popping up.  No change in the loading to grub rescue mode.

Running a diagnostic from the boot menu (F12) gave the following error:

> Error Code 0146.
Msg: Error code 2000-0146
Msg: Hard Drive 0 - self test log contains previous error(s)
The give error code and message can be used by Technical 
Support to help diagnose the problem.

Pouring over forum threads, how to's, and wiki's has not gotten me answers.

I would appreciate some expertise on how to fix the problem.  I'm REALLY hoping replacing the hdd is not the solution given that the drive is only 3 months old....and I don't have the drive backed up.


[SIZE=3]**Thanks for any help!!**[/SIZE]

Ed

---

### Post by Edward_Marquardt on 2016-01-31
**BUMP**

I guess its a bad sign when nobody knows the answer!

---

### Post by leunam12 on 2016-02-01
Hard drives fail very easily, have you checked the disk's health with the "Disks" application? Maybe it's time to replace that drive

---

### Post by oldfred on 2016-02-01
Often the shutdown while system is still running even if hung is the creator of the problem. But usually then fsck fixes it.

Best to always remember the skinny elephants:
 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

If you have good backups, some of these last ditch options may be something to try.

 Last ditch redo superblocks:
[http://ubuntuforums.org/showthread.php?t=1681972&page=5](http://ubuntuforums.org/showthread.php?t=1681972&page=5)
Worked for this user:
[http://ubuntuforums.org/showthread.php?t=2033778](http://ubuntuforums.org/showthread.php?t=2033778)
[http://ubuntuforums.org/showthread.php?t=1684746](http://ubuntuforums.org/showthread.php?t=1684746)
Some additional advanced ways:
[http://animeshdas.wordpress.com/2009/11/18/data-recovery-from-corrupted-ext2ext3-filesystem-having-bad-superblock/](http://animeshdas.wordpress.com/2009/11/18/data-recovery-from-corrupted-ext2ext3-filesystem-having-bad-superblock/)
[http://www.hanksaves.com/hddrecovery/index.php/Welcome_to_Hank%27s_Data_Recovery_Wiki](http://www.hanksaves.com/hddrecovery/index.php/Welcome_to_Hank%27s_Data_Recovery_Wiki)

---

### Post by Edward_Marquardt on 2016-02-06
In DISKS I get the following

>  Disk is OK, 5704960 bad sectors (29° C / 84° F) 

If I run a Self-Test then I get a message about Self-Test Failed due to "Threshold not exceeded".

The hard drive is less than three months old, I was expecting to get a little more out of it.....

---

### Post by oldfred on 2016-02-06
I do not understand why it says disk is OK, if you have that many bad sectors?

But generally a few bad sectors is not the end, but a growing number of bad sectors indicates drive is failing.

---

