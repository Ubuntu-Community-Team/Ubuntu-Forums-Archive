---
title: "Dual booting Hardy &amp; Gutsy"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by baracuda68 on 2008-04-25
Hi.
I had WinXP on hda1, and currently 7.10 on hdb1. I decided to install 8.04 
on (over)the Windows drive, since I never used it. After I installed 8.04, I need to edit my current GRUB which is on my 7.10 install. How should I properly do this? - Also, my Hardy install detected my drives as "SCSI", which they are not. I have no SCSI devices, no RAID. They are not even SATA, they are ATA EIDE  drives, but they are being called "sda" drives. Is this an issue?

thanks.:confused:

---

### Post by dondad on 2008-04-25
> **baracuda68 said:**
> Hi.
I had WinXP on hda1, and currently 7.10 on hdb1. I decided to install 8.04 
on (over)the Windows drive, since I never used it. After I installed 8.04, I need to edit my current GRUB which is on my 7.10 install. How should I properly do this? - Also, my Hardy install detected my drives as "SCSI", which they are not. I have no SCSI devices, no RAID. They are not even SATA, they are ATA EIDE  drives, but they are being called "sda" drives. Is this an issue?

thanks.:confused:

If you installed hardy last, it will be using the grub menu from the hardy install. I have both gutsy and hardy installed, and for various reasons, I reinstalled gutsy afterwards. I had to update the uuid's and kernel info in the gutsy grub menu because that is the one it is using. Whenever hardy does a kernel upgrade, I have to modify the gutsy menu to reflect that.

---

### Post by baracuda68 on 2008-04-25
When I installed Hardy, I got some error about not able to install GRUB. I thought it might be a conflict with Gutsy's GRUB :(

---

### Post by Paqman on 2008-04-26
> **baracuda68 said:**
> Hi.
I had WinXP on hda1, and currently 7.10 on hdb1. I decided to install 8.04 
on (over)the Windows drive, since I never used it. After I installed 8.04, I need to edit my current GRUB which is on my 7.10 install. How should I properly do this?

```

grub
root (hd0,0)
setup (hd0)
quit

```
This would set Grub up to use the menu.lst on sda1. Grub starts counting from 0, so sda1 is hd0, partition 0.
But, if you're seeing both Gutsy and Hardy in GRUB then you've already got it set up this way.

> 
 - Also, my Hardy install detected my drives as "SCSI"...Is this an issue?

Nope. It's just one of those things.

---

### Post by MaddMatt on 2008-04-26
Just try adding the menu.list entries that are missing from your gusty menu.list... it's what I had to do. Probably a bug with the OS detection that worked so well in previous releases.

---

### Post by baracuda68 on 2008-04-26
Ok.
Here's what I did.
I disconnected hdb (with my 7.10 on it) and reinstalled 8.04 on hda/sda by itself.
Then re-connected hdb, rebooted, mounted hdb,while I was in 8.04, edited my /boot/menu.lst with my copy/pasted grub info from 7.10.

Works Great!
Thanks to all!
Marked as solved!:guitar:

---

