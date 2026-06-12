---
title: "Ubuntu 16.04 LTS does not see Windows 10 partitions"
date: 2018-03-25
forum: New to Ubuntu
---

### Post by elnur92 on 2018-03-25
I installed Ubuntu 16.04 LTS on the external hard disk (1 TB size). I  have a laptop with Windows 10. Windows 10 is set on the 512 GB disk.  After entering Ubuntu, I can't see (access) the Windows 10 partitions.  Somewhere on the Internet someone wrote that the possible solution is  turning off quick start of Windows. I turned off quick start in BIOS and  also in Windows power settings but it didn't help. In Ubuntu, I opened  "disks" tool, and it shows me the Windows disk with partitions but there  is no information (it writes "Unknown") about file system of two  partitions (partition 3 and partition 4) which correspond to "C" (system  files) and "D" (data). I attach the prtscr of "disks" window. Please  advise me what I can do to solve this problem.

[ATTACH=CONFIG]279082[/ATTACH][ATTACH=CONFIG]279083[/ATTACH][ATTACH=CONFIG]279084[/ATTACH][ATTACH=CONFIG]279085[/ATTACH][ATTACH=CONFIG]279086[/ATTACH]

---

### Post by oldfred on 2018-03-25
Is this what you turned off?
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Also if Windows needs chkdsk or other repairs, the Linux NTFS driver will not mount the partition to prevent further damage.
 
FYI

 Redhat depreciating btrfs
[http://www.phoronix.com/scan.php?page=news_item&px=Stratis-Red-Hat-Project](http://www.phoronix.com/scan.php?page=news_item&px=Stratis-Red-Hat-Project)
Linux 4.11 File-System Tests: EXT4, F2FS, XFS & Btrfs
[http://www.phoronix.com/scan.php?page=article&item=linux-411-fs&num=1](http://www.phoronix.com/scan.php?page=article&item=linux-411-fs&num=1)

---

### Post by elnur92 on 2018-03-25
Yes, it is. But it doesn't give any result. Also I have now one more problem - when I try to start Windows 10 it requires to enter BitLocker key, and so, every time when I want to enter Windows, I need to go to the official site (using my mobile) where I can get the key. The laptop is Lenovo Thinkpad 5th gen. I wouldn't like to switch off BitLocker encryption but it seems that I should do that and check whether it helps to solve two problems simultaneously: 1) access to Windows partitions within Ubuntu; 2) entering Windows without BitLocker key.

> **oldfred said:**
> Is this what you turned off?
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Also if Windows needs chkdsk or other repairs, the Linux NTFS driver will not mount the partition to prevent further damage.
 
FYI

 Redhat depreciating btrfs
[http://www.phoronix.com/scan.php?page=news_item&px=Stratis-Red-Hat-Project](http://www.phoronix.com/scan.php?page=news_item&px=Stratis-Red-Hat-Project)
Linux 4.11 File-System Tests: EXT4, F2FS, XFS & Btrfs
[http://www.phoronix.com/scan.php?page=article&item=linux-411-fs&num=1](http://www.phoronix.com/scan.php?page=article&item=linux-411-fs&num=1)

---

### Post by oldfred on 2018-03-25
I do not think from grub or Ubuntu you can open Windows encrypted partitions. There is not a bitlocker Linux driver as far as I know.
You could create a smaller NTFS shared partition. Does then Windows let you not include that in its bitlocker or is it a full drive (all Windows partitions) encryption?

---

### Post by elnur92 on 2018-03-25
Eventually I coped with two problems by disabling the BitLocker encryption in Windows. So now I can enter Windows without any BitLocker recovery key and I can see Windows partitions within Ubuntu (in the launcher). I attach the prtscr of "disks" tool in Ubuntu - the information about Windows partitions appeared (file system NTFS is recognized).
But one more problem occured (I don't know when this chain of problems finishes). From time to time, when shutting down (or restarting) either Windows or Ubuntu, my laptop doesn't shut down, it suspends (or may be "hangs" will be more correct to say), the screen becomes black and nothing happens. In this case, I have to push and hold power button in order to turn off computer. What can cause such a trouble? May it be somewhat related to USB connection by which the external hard disk is connected to the laptop?

[ATTACH=CONFIG]279095[/ATTACH]

> **oldfred said:**
> I do not think from grub or Ubuntu you can open Windows encrypted partitions. There is not a bitlocker Linux driver as far as I know.
You could create a smaller NTFS shared partition. Does then Windows let you not include that in its bitlocker or is it a full drive (all Windows partitions) encryption?

---

### Post by oldfred on 2018-03-25
Best not to do a hard shutdown.

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

But it could be related to USB drive.

I have some full installs on flash drives and just copying data, system can say it is done, but flash drive led is still flickering. So I wait until sure there is no activity.

---

### Post by elnur92 on 2018-03-26
Thank you very much for help!

> **oldfred said:**
> Best not to do a hard shutdown.

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

But it could be related to USB drive.

I have some full installs on flash drives and just copying data, system can say it is done, but flash drive led is still flickering. So I wait until sure there is no activity.

---

