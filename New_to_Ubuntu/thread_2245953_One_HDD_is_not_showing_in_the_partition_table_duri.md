---
title: "One HDD is not showing in the partition table during install"
date: 2014-09-27
forum: New to Ubuntu
---

### Post by J0nDaFr3aK on 2014-09-27
Hi,
I'd like to install Lubuntu on my pc on a secondary hard drive (Windows 8.1 is on the primary SSD). I have 1 SSD and 2 hard disks. In the partition table I can only see the SSD and the 1TB drive, which I'll leave as data storage. I have one more 250GB drive, which is not displayed, yet it is mounted and I can access it from the file browser. Why isn't the drive displayed?

---

### Post by J0nDaFr3aK on 2014-09-27
Update: I formatted the hard drive to ext4 and reserved 4 gigs of space for the swap partition using gparted. The drive won't still show up in the partition manager while trying to install Lubuntu

---

### Post by Vladlenin5000 on 2014-09-27
How are the disks connected?
A disk in an add-on SATA card, for example, may not be recognized by BIOS/UEFI but only in the OS.

---

### Post by J0nDaFr3aK on 2014-09-27
> **Vladlenin5000 said:**
> How are the disks connected?
A disk in an add-on SATA card, for example, may not be recognized by BIOS/UEFI but only in the OS.

The disks are connected in ahci mode. I can see all the 3 disks both in bios and in the OS. I tried to mount the disk by typing in the terminal sudo mount /dev/sda /media/sda - t ext4 but it returns an error message,  that the file system is isw_raid_member. I tried then to format to ext3 but still won't work. It's sda because I disconnected the other 2 disks.. In gparted, the option "mount" for the disk is grayed out

---

### Post by oldfred on 2014-09-27
Was drive once part of RAID set?
Drive then may have meta-data on it and that causes issues as installer thinks it is RAID and does not want to use that.

If sure it not RAID.
       Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

---

### Post by J0nDaFr3aK on 2014-09-28
> **oldfred said:**
> Was drive once part of RAID set?
Drive then may have meta-data on it and that causes issues as installer thinks it is RAID and does not want to use that.

If sure it not RAID.
       Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

It worked!!! thank you lots! The hdd used to be part of a raid 0 array, but after that I switched back to a single disk configuration and it's always worked ever since!

Thanks again!

---

