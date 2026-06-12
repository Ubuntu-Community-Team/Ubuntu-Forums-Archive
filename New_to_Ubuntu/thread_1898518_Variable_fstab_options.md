---
title: "Variable fstab options"
date: 2011-12-21
forum: New to Ubuntu
---

### Post by patman0623 on 2011-12-21
I have a system where I am frequently changing my drive order due to a lack of computer cables.

This is how my drive appears when I have the backup hard drive plugged in:
Backup drive -> dev/sda
Ubuntu/Windows drive -> dev/sdb

This is how my drive appears when I unplug the backup and plug in my dvd/cd:
Ubuntu/Windows drive -> dev/sda
CD/DVD drive -> /dev/sr0

This present a problem with my fstab, in that it can't mount my Windows drive; this is bad because I keep a lot of my documents and music there.

My fstab file reads as the following:
[FONT="Courier New"][SIZE="1"]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=93...45 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
#UUID=3d...53 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
#UUID=5c...97 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/mapper/cryptswap2 none swap sw 0 0

/dev/sda1 /mnt/backup  auto owner,exec,rw,async
/dev/sda2 /mnt/olddrv  auto owner,exec,rw,async
/dev/sdb2 /mnt/windows  auto owner,exec,rw,async
/dev/sdb4 /mnt/windows-backup  auto owner,exec,rw,async[/SIZE][/FONT]

How can I change the last two values from "sdb2/sdb4" so that the system will mount it properly?

---

### Post by Ocxic on 2011-12-21
Remove the entries for your windows drives, they should auto mount and you won't have to worry about it.

---

### Post by m_duck on 2011-12-21
The top of your fstab hints at 'a more robust way' to name devices. Run **sudo blkid** and it will give you the UUID of the partitions in question. The UUID won't change unless the partition itself is changed, and therefore will remain the same whether your backup drive is plugged in or not. Before changing anything, backup your current fstab (in case things go wonky) and then simply replace /dev/sda1, /dev/sda2 etc in fstab with UUID=the-uuid-you-obtained.

---

### Post by mcduck on 2011-12-21
+1 to above. Use either the UUID of a partition, or it's label (if you've set one), to point to a specific partititon instead of the device name which might change depending on the connected drives and the order in which they are recognized by the system.

This is quite important when dealing with removable drives in fstab, but can also be necessary on some systems for internal drives as well.

---

### Post by patman0623 on 2011-12-21
> **m_duck said:**
> The top of your fstab hints at 'a more robust way' to name devices. Run **sudo blkid** and it will give you the UUID of the partitions in question. The UUID won't change unless the partition itself is changed, and therefore will remain the same whether your backup drive is plugged in or not. Before changing anything, backup your current fstab (in case things go wonky) and then simply replace /dev/sda1, /dev/sda2 etc in fstab with UUID=the-uuid-you-obtained.This work brilliantly, thank you. Even better, I used the label option, so that if I change a partition, it will still mount.

> **Ocxic said:**
> Remove the entries for your windows drives, they should auto mount and you won't have to worry about it.I'm still intrigued about this, though; how does Ubuntu automatically mount Windows drives?

---

