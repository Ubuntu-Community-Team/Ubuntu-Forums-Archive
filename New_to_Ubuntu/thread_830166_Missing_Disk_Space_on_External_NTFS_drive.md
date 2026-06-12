---
title: "Missing Disk Space on External NTFS drive"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by SHB2 on 2008-06-15
Hope someone can help me on this one as it's driving me potty!

Just bought a Maxtor External HDD formatted in NTFS which I'm using to backup my data with. Everything worked fine until my PC crashed during the data transfer.

Now, when I select Properties, I can see 156GB of files but it is saying 246GB has been used. Had a quick look in gparted and that's telling me that 246GB has been used but when I do sudo du -h it only comes to just over 156GB.

As far as I can see there aren't any hidden files. I'm just wondering if it's an issue with my trash as when I delete a file on the external HDD it doesn't seem to go to my wastebasket.

Any help would be most gratefully received!!!

---

### Post by subaruwrc01 on 2008-06-15
The external crashed during the transfer.  You'll have to reformat it.

---

### Post by SHB2 on 2008-06-15
Argh. That's what I feared. Is there really no other way to fix it without formatting the whole hard drive? Luckily I have the data elsewhere but I've spent most of the day backing it up already!

---

### Post by vanadium on 2008-06-15
Obviously reformatting the hard disk would be the very last rescue. Very likely, the disk can be repaired doing a disk check. Connec the disk to a system running ms-windows and check it using the windows tools. Then disconnect it safely, using the "Safely remove devices" icon in the Windows task bar. (Because ntfs is a proprietary format of Microsoft Linux cannot fully check and repair ntfs).

---

### Post by SHB2 on 2008-06-15
Thanks - was thinking along the same lines myself. Sadly XP, Disk Management and External HDD's don't always work very well which meant this couldn't work either. Anyway, I've formatted the hard drive and in the process of copying back across - here's hoping it goes a bit smoother this time!

---

### Post by vanadium on 2008-06-18
Indeed, if you have the data elsewhere, reformatting is a thorough solution anyway and you do not depend on another operating system. If you do not regularly need to access the data from different Windows systems, you could have formatted as ext3 as a solid, crash resistant file system that can be coped with fully from within Linux.

---

