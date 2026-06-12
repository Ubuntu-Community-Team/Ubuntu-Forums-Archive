---
title: "installation problem"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by yusufsani on 2008-08-30
HI

please i am new to linux , i have a laptop with Xp and i installed Fedora 7 now i want remove it and replace it with ubuntu , my hard disk is 160, 60 for the Xp and 100 for the fedora ,but please i want to adjust it to 100 for XP and 60 for the Ubuntu

thanks

---

### Post by MasterSander on 2008-08-30
You could download the gparted live cd, works great for editing partitions/ making new ones etc. Also, when ubuntu asks you if you would like to install grub make sure you answer yes.

---

### Post by az on 2008-08-30
> **yusufsani said:**
> HI

please i am new to linux , i have a laptop with Xp and i installed Fedora 7 now i want remove it and replace it with ubuntu , my hard disk is 160, 60 for the Xp and 100 for the fedora ,but please i want to adjust it to 100 for XP and 60 for the Ubuntu

thanks

Boot the Ubuntu desktop cd and click on the installation icon.

At the partitioning step, select "manual" and delete the fedora partitions.  Resize your XP partition to 100 Gigs and leave the deleted partition from Fedora as FREE SPACE.  Click Back to start the partition step again and use "guide partitioning - use largest free space" and continue.

If you get stuck at the resizing step for XP, you will need to defragment it in Windows - so on second thought, shrink it first (before deleting Fedora).  If you have trouble, you will still be able to boot using grub that way.  Once you have defragmented, boot the Ubuntu CD again and start over.

---

### Post by MasterSander on 2008-08-30
> **az said:**
> Boot the Ubuntu desktop cd and click on the installation icon.

At the partitioning step, select "manual" and delete the fedora partitions.  Resize your XP partition to 100 Gigs and leave the deleted partition from Fedora as FREE SPACE.  Click Back to start the partition step again and use "guide partitioning - use largest free space" and continue.

If you get stuck at the resizing step for XP, you will need to defragment it in Windows - so on second thought, shrink it first (before deleting Fedora).  If you have trouble, you will still be able to boot using grub that way.  Once you have defragmented, boot the Ubuntu CD again and start over.

I don't think you can resize it in the manual partition editor of the ubuntu cd and then go back, ubuntu will tell you you didn't select a swap partition and you also forgot to pick a / partition. That's why it's better to use the gparted live cd, no need to defragment xp either, which would be needed if you would resize in xp.

---

### Post by ugm6hr on 2008-08-30
> **MasterSander said:**
> I don't think you can resize it in the manual partition editor of the ubuntu cd and then go back, ubuntu will tell you you didn't select a swap partition and you also forgot to pick a / partition. That's why it's better to use the gparted live cd, no need to defragment xp either, which would be needed if you would resize in xp.

Ubuntu LiveCD has GParted installed too.  The version is 0.3.5, which should be OK for this purpose.

So - just boot Ubuntu LiveCD & start GParted (System-> Administation-> Partition Editor).

Resize XP, delete Fedora partitions (inc swap).

Then run the Ubuntu installer.  You could then just use the automated (Use largest free space option), or manual installation (if you want a separate /home etc) options depending on preference.

NB: resizing partitions can jeopardise data - so always backup first.

---

