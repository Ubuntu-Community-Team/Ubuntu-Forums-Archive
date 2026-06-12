---
title: "Lost D Drive"
date: 2012-06-15
forum: New to Ubuntu
---

### Post by medcalf1857 on 2012-06-15
Hello all.  yesterday I installed Ubuntu on my desktop.  The machine has a slave D drive and unbeknown to me as I went through the installation it has installed the OS on the D drive.  I allowed the installtion to partition the drive (I thought it was C at the time) Half and half, its 500GB.  After the installation I rebooted and it went straight to windows as there was no dual boot the new OS being on D.  It wasn't until I had a look around that I realised that D was now split. and showed about 250GB.  At this point I could see the D drive in windows explorer with both halves of the logical drives also shown in disc manager.  I tried to delete the Ubuntu drive but that was refused in disc manager.  I left it for a think about it and have come back to the computer this morning and cannot now see the d drive at all in either disc manager or windows explorer??  Can anyone suggest a course of action please?  It as if someone has stolen my D drive.

---

### Post by Linux_junkie on 2012-06-15
As you have installed Ubuntu I am assuming you have a live CD or USB stick.  Boot your computer using the live media in to Ubuntu then from Ubuntu run gparted.  It should display all dicks and partitions available.  Select the disk or partition you want to blank then simply format to NTFS or delete partition.

---

### Post by mapes12 on 2012-06-15
This neat little tool may help:-

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

