---
title: "Can I run a distro ISO off my hdd?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by Lolicon on 2008-05-10
I don't have any CDs at the moment, is there something to allow me to run an iso off my hdd? I have ext3 and ntfs partitions if it makes a difference.

---

### Post by Joeb454 on 2008-05-10
I don't think it is possible to run an ISO from your hard drive in the way you are asking, unless you do it in a virtual machine.

What I mean is, I don't think you can actually boot your PC from it :)

---

### Post by Lolicon on 2008-05-10
i seem to recall there was a thread on how to do it, but i cant really find it because of the new forum not autosearching.

---

### Post by zvacet on 2008-05-10
Are you looking for [this]("http://ubuntuforums.org/showthread.php?t=666267&highlight=iso")?

---

### Post by Journeyman on 2008-05-10
You can mount an iso using ```
 mount -o loop disk1.iso /mnt/disk 
```  You can't boot from it, but you can access it.

---

