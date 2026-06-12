---
title: "how do I give old linux partition back to xp"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by kklemperal on 2008-06-23
Sorry if the title wasn't all that clear.  I uninstalled a linux distro by deleting the partitions.  Now I have a couple partitions (one used to be the main linux partition, the other one was the grub) that are unallocated and I'm wondering how I can make them part of my main system C partition.

---

### Post by AndyCee on 2008-06-23
You can boot into a liveCD, enter the partition manager and expand the XP partition in there. It will give you a nice graphical idea of the disk's allocations. If you move a partition, it may take a long time.

Be careful, of course.

---

### Post by rbanavara on 2008-06-23
If you just delete the linux partition, you may have problems in booting. If you dont have this issue (or already handled this), fine. If not you may have to use fixmbr from the xp install disk from recovery console.

To add the space back to XP, you may use any of the partition managers like partition magic / gparted. I would prefer gparted. its there on your ubuntu live CD. once the partitions to the right of your XP partition are dropped (I assume those were linux partition), you can resize the XP partition from there. You might be forced to run chkdisk on first boot to XP after this.

(All disk operations through gparted may have its own consequences, its better to backup your valuable data before you attempt this).

---

### Post by thisiam on 2008-06-23
hirens boot cd will have alot of different partition sofware that you can use to delete the linux partition and re size the C: drive to add the empty space.

---

### Post by bumanie on 2008-06-23
Easy if it was purely a data partition ie follow as above. If it was a bootable partition with grub on it you will have to do the expansion and then probably have to fixboot and fixmbr via console in windows if grub has been installed to the windows mbr. How to do this depends on your setup. If you have a windows disk, use that; if you have a restore partition, you will have to restore the mbr that way; if you have neither you will have to use something like super grub disk or testdisk that can write 'windows-like' boot sectors.

---

