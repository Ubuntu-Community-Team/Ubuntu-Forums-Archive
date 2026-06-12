---
title: "Installing a new Ubuntu installation on a new hard drive"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by JoshMH on 2008-11-26
Hi, I just recently purchased a new hard drive for my system to install Ubuntu on and in my system I already have 3 hard drives set up in RAID 5 for my Vista OS. How would i go about installing this new hard drive and Ubuntu without messing up my computer.

---

### Post by JoshMH on 2008-11-26
bump

---

### Post by mapes12 on 2008-11-26
Your system should "see" your Raid array as one single drive. You don't say how the Raid array is managed i.e. by software or hardware. In either case you will need to make sure that the new drive, once installed, is not included in the Raid array. It shouldn't be because Raid 5 generally uses 3 disks as a default but I would check it out first. Once you know that the disk is not in the Raid array then go ahead and do the Ubu install making sure that you select the correct HDD to install to. Grub should identify the windoze NTFS MBR and create a dual boot environment.

BACKUP your windoze stuff before you start!

---

