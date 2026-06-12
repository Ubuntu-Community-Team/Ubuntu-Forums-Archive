---
title: "Mount routine for Backupdrive"
date: 2013-03-26
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2013-03-26
What is needed to make a routine to mount my Backupdrive (sdb1), which is strictly for archiving/backups? I understand it is best to not leave it mounted or not to automatically invoke mounting at each boot.

Also, having trouble configuring Fstab for a sdb5 partition; i believe the problem is in the partition labeling. Where am I screwing up?

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# set up home pointer to /home
UUID=3d34262b-e98a-441c-bc7a-e3a3989d1378 /home ext3 defaults,errors=remount-ro 0 2
# set up Backupdrive Sdb1
UUID=7a117704-c5b0-4858-92c4-16e95deb55f9 /media/Backupdrive ext3 defaults,errors=remount-ro 0 2

# 
# set up Drive 2: sdb5 
UUID="07cbf7e3-e34c-429a-b26a-00dbe44a9884 /media/Drive 2: sdb5 ext3 defaults,errors=remount-ro 0 2
#  

# / was on /dev/sda7 during installation
UUID=ba167dfa-471a-4ee5-940e-7c67e3931ce3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2a8810b8-d6e6-4c2b-a89c-fb345ca0a122 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

****************************************************************************************************************************
Device listing:

/dev/sda1: UUID="30182B1D182AE218" TYPE="ntfs" 
/dev/sda5: LABEL="HOME" UUID="3d34262b-e98a-441c-bc7a-e3a3989d1378" TYPE="ext3" 
/dev/sda6: UUID="2a8810b8-d6e6-4c2b-a89c-fb345ca0a122" TYPE="swap" 
/dev/sda7: UUID="ba167dfa-471a-4ee5-940e-7c67e3931ce3" TYPE="ext4" 
/dev/sdb1: LABEL="Backupdrive" UUID="7a117704-c5b0-4858-92c4-16e95deb55f9" TYPE="ext3" 
/dev/sdb5: LABEL="Drive 2: sdb5" UUID="07cbf7e3-e34c-429a-b26a-00dbe44a9884" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="4CB9BA847381C91A" TYPE="ntfs"

---

### Post by ozark_hillbilly on 2013-03-28
bump

---

### Post by Morbius1 on 2013-03-29
The easy one first:
>  UUID="07cbf7e3-e34c-429a-b26a-00dbe44a9884 /media/Drive 2: sdb5 ext3 defaults,errors=remount-ro 0 2
** You have  a beginning quote mark but no end quote - so just remove the first quote.
** You have a space - maybe 2 - in the mount point that must be replaced with a \040 for the system to read it properly. So it becomes:
```
/media/Drive\0402:\040sdb5
```
For my money I would just create a new mount point without any spaces or weird characters like ":":
```
sudo mkdir /media/Drive2
```
Then change the fstab entry to this:
```
 UUID=07cbf7e3-e34c-429a-b26a-00dbe44a9884 /media/Drive2 ext3 defaults,errors=remount-ro 0 2
```
This I don't understand:
> What is needed to make a routine to mount my Backupdrive (sdb1), which  is strictly for archiving/backups? I understand it is best to not leave  it mounted or not to automatically invoke mounting at each boot.
If you don't want it to automount then why add an entry in fstab? It will by default mount to /media/LABEL which in this case is /media/Backupdrive when selected in Nautilus.

---

### Post by ozark_hillbilly on 2013-04-02
Thanks Morbius. I will try your suggestions.

---

