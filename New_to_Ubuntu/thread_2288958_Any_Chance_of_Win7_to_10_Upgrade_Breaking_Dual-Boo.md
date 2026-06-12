---
title: "Any Chance of Win7 to 10 Upgrade Breaking Dual-Boot w/Buntu's?"
date: 2015-07-31
forum: New to Ubuntu
---

### Post by Geoffrey_Arndt on 2015-07-31
Haven't heard if Win7 or 8 upgrade to 10 could result in a broken dual boot with Ubuntu or any linux distro . . . ??  Any thoughts or info available yet?

---

### Post by NathanRodriguez on 2015-07-31
Yes, probably will as Windows 7 replaced the dual boot schematics on my machine. But you can restore it using a bootable Ubuntu disk or Usb.

---

### Post by cariboo on 2015-07-31
I downloaded windows 10 following instructions[ here]("http://www.cnet.com/how-to/heres-how-to-upgrade-to-windows-10/"), then did a custom installation. You really have to know your partition scheme, as you have to install to the partition your Windows install was originally on. Once done, you should be able to boot the same way you normally do.

---

### Post by oldfred on 2015-07-31
Just saw a couple of users with BIOS installs and Ubuntu as a logical partition in the extended partition with major issues. It may depend on whether your ext4 partition is primary or logical.

Windows has many times rewritten partition table on major update or reinstall. But it leaves off Linux partitions in the extended partition. It does usually rewrite swap. Then inside the extended is a large gap of unallocated space. Testdisk can usually restore it and system even has booted without other repairs in some cases. Others either could not restore correct partition or had made other changes and could not get system working.

Best to document partitions if MBR(msdos). If you make no changes to partition sizes then you can easily restore partitions.
       Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

To restore from PTsda.txt
 sudo sfdisk --no-reread -f /dev/sda -O PTsda.save < PTsda.txt
"--no-reread" means don't check if disk is unmounted
-f force
"-O PT.save" means save a backup of original partition table in PT.save. PT.save is in binary format.

In addition to testdisk, you may be able to use parted rescue.
Use parted rescue to restore missing partition details in post #22
[URL="http://ubuntuforums.org/showthread.php?t=1775331"]http://ubuntuforums.org/showthread.php?t=1775331


[/URL]

---

### Post by Geoffrey_Arndt on 2015-07-31
Thanks to all for the info . . .  somehow I suspected this and so it isn't surprising.  Perhaps this thread will save a few folks some real headaches or worse.

 As I no longer need to run "any" version of Windows,  I'll gladly pass on the "opportunity" to upgrade.  ;)

---

