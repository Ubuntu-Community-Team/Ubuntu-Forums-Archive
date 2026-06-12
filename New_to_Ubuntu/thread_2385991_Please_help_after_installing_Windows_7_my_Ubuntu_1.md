---
title: "Please help after installing Windows 7 my Ubuntu 16.04 became unaccessible"
date: 2018-02-27
forum: New to Ubuntu
---

### Post by sergeevleva63 on 2018-02-27
Please help - have this configuration 2 HDDs on one of them (120 gig) Ubuntu 16.04 was installed and i have been working on it. After  i installed Windows 7 on another drive that i have on this computer - 80 gig one, ubuntu stopped loading and the system began starting just on Windows (grub was just wiped out i guess by Evil 7). After that, trying to restore access to the 120 gig Ubuntu 16.04 drive i installed a copy of U16.04 on the drive where Windows 7 got installed, as a second system. It installed fine with a grub but it didnt restore access to the 120 gig drive. However i was able to see it in Ubuntu as mounted when i started that copy i installed along W7 on 80 gig drive. I should have backed up files at that point of time but i misplaced the passphrase i had for encrypted home folder so i continued trying to restore access by rewriting mbr in BootIce which didnt do it. Please help, here is the link to the boot-repair standard procedure which also didnt do any good redtoring the access. I need to at least get it mounted and pull the info from it (found the passphrase) thank you all for the help! [http://paste.ubuntu.com/p/MMjbkbJj8D/](http://paste.ubuntu.com/p/MMjbkbJj8D/)

---

### Post by sergeevleva63 on 2018-02-27
Also - when i was trying to mount the 120 gig drive with: sudo mount /dev/sdb /mnt it says "wrong fs type, bad option, bad superblock"

---

### Post by yancek on 2018-02-27
Try changing the boot priority to set the 120GB drive first as it shows Grub properly installed.  If it boots Ubuntu, run sudo update-grub and watch the output for windows.  This drive shows an entry for Ubuntu 8.10??  

If you can boot the Ubuntu on the first drive where you also have windows, you could boot that and update-grub and you should get an entry for the Ubuntu on the other drive.
[h=3][/h]

---

### Post by sergeevleva63 on 2018-02-28
Well there was a previous version of Ubuntu installed on the 80 gig drive where W7 and U16.04 installed right now, yes i think it was the version you mentioned in your post. When i do a force boot from 120 gig drive (after i ran update-grub) it says 
error: no such device: 30f4d13f-da7f-4b25-b1fa-1380f15306a6 
entering rescue mode ... 
Grub rescue>

I dont know what to do, mr.Gates just destroyed a product of 4 years of hard work in form of 80 gig of info i backed up on the 120 gig drive.

---

### Post by oldfred on 2018-02-28
This is a major problem you have to resolve first from sdb.

```
Extended partition linking to another extended partition.
```

It then is not showing sdb1 as Linux partition, but has some random data in partition table as ID 93  - Amoeba/Accidently Hidden Linux? 

Do this for both sdb & sda, just in case.

 backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sdb > PT_sdb.txt
So you know sectors:
sudo parted /dev/sdb unit s print 

      
 sudo fdisk /dev/sdb

Then see if a w writes correct partition table. Not sure with newest fstab what it does.

---

### Post by sergeevleva63 on 2018-02-28
Yes, I will definately do what you [COLOR=#000000]oldfred [/COLOR]are suggesting as far as linking partitions. Here is some more info that might help - when I was trying to restore access I wrote an MBR on sdb using Bootice. Also i tried to restore superblock from a backup file it supposedly stores on the drive itself (don't remember the code smth from the Internet). Also made sdb1 partition active in Bootice. Yesterday tried to restore from grub rescue (picture attached). When I was doing this i disconnected the other drive to make sure i work just with the drive that i need to restore access to.

---

### Post by sergeevleva63 on 2018-03-02
Hello all, I did what you Oldfred had advised, but unfortunatelly it didn't succeed, after I completed the instructed it again showed me 

[COLOR=#000000]error: no such device: 30f4d13f-da7f-4b25-b1fa-1380f15306a6 [/COLOR]
[COLOR=#000000]entering rescue mode ... [/COLOR]
[COLOR=#000000]Grub rescue>

Screenshots of output are attached. I did this command [/COLOR][COLOR=#000000]sudo fdisk /dev/sdb [/COLOR][COLOR=#000000]only for the sdb though. I don't know maybe that affected.
And yes "w" did work writing a partition table.



[/COLOR]

---

### Post by oldfred on 2018-03-02
What brand/model system?
Is UEFI/BIOS have drives set for AHCI, not IDE nor RAID?

Try Boot-Repair again.
With partition error, you could not even run fixes, but maybe they will work?

---

