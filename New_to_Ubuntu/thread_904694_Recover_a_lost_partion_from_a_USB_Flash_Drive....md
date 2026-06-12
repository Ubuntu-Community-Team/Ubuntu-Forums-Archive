---
title: "Recover a lost partion from a USB Flash Drive..."
date: 2008-08-29
forum: New to Ubuntu
---

### Post by bronner on 2008-08-29
What would be the best way (if possible) to recover a deleted default partition off of a flash drive that has recently been reformatted using Ubuntu? Thanks again.

---

### Post by nicedude on 2008-08-29
You could try installing testdisk from the repositories as it is a partition recovery and fixing program and see if it can retrieve it. Is there data on it that you desperatly need because if not you chould be able to just delete any partitions on it and repartition and format it however you like with NTFS or FAT32 so you can use with both Linux and Windows PC's easily without additional software.

Hope you get it going and hope this helps

---

### Post by bronner on 2008-08-29
Cool thanks, I'll give it a shot.

---

### Post by Barrucadu on 2008-08-29
If testdisk can't recover it (as it couldn't for me a while ago with an important partition), you can edit the partition table manually with sfdisk. It is a fairly complex piece of software though, so read and understand the manpage several times if you go that route.

---

