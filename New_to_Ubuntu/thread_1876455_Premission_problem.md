---
title: "Premission problem"
date: 2011-11-06
forum: New to Ubuntu
---

### Post by jonaskeldusis on 2011-11-06
I am the owner of Ubuntu 10.11. Files, an external hard drive suddenly had to premissed as only to read. I tried to change the permission, but I got a message that there is an error in determining the rights. Ended in failure. May I ask for help.:confused:

---

### Post by qwertycvc on 2011-11-06
Try using <[COLOR=Red]sudo nautilus[/COLOR]> in the terminal window. It gives you absolute power..but understand that you will be able to modify anything including system files which whill be risky

---

### Post by Kyoushuu on 2011-11-06
> **jonaskeldusis said:**
> I am the owner of Ubuntu 10.11. Files, an external hard drive suddenly had to premissed as only to read. I tried to change the permission, but I got a message that there is an error in determining the rights. Ended in failure. May I ask for help.:confused:
What is the type of the filesystem? FAT or ext4 or what?

If ext4/ext3/ext2, open a terminal then run:
```
sudo chown -R <username>:<username> <mount point>
```
Replace <username> with your username and <mount point> with the mount point of drive, something like "/media/drive". Put the mount point in double quotes (") if it has some spaces, i.e.:
```
sudo chown -R jonaskeldusis:jonaskeldusis "/media/Ubuntu 10.11. Files"
```

Open Disk Utility if you don't know the filesystem type.

---

### Post by Mark Phelps on 2011-11-06
I'd read that NTFS formatted partitions will default to read-only if there is a problem with the integrity of the filesystem -- which can happen very easily with external drives if you simply unplug them or turn them off, without first safely removing them.

To check the filesystems on the drive, next time it is connected, open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one).  It will list out the partitions on the drives.

---

