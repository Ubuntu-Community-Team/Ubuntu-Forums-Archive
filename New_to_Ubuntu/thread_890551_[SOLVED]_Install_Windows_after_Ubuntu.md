---
title: "[SOLVED] Install Windows after Ubuntu"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by zzzonked on 2008-08-15
When I first installed Linux, this was the partition I did: 30GB NTFS/about 20GB FAT32/20GB Ext3/1GB swap. Then I had less than 1GB of unused space left on my hard drive, don't ask me why it's only 71GB, I dunno, it's just like that :p

All the partitions were empty after I did this because I somehow killed everything during the partitioning process, but it was okay because I backed up everything on a thumb drive.

I installed Linux on the third partition, and left the other 2 empty. Then after I've got Linux configured and stuff, I copied everything from the thumb drive into the second partition.

Now I want to install Windows in the first partition, and only the first, is this possible without killing anything else I already have? (Somehow the first and second partitions are labeled as "media" in Ubuntu, is this normal?)

---

### Post by tzulberti on 2008-08-15
You can install windows in the first partition, but the problem is that Windows (at least XP) deletes the grub, so after you installed Windows you will have to restore grub to boot into linux.

---

### Post by zzzonked on 2008-08-15
To be very honest, I have no idea what grub is, but I see it every time I boot. So what is it? So does this mean that Windows won't kill anything I already have (other than grub)? And how do I restore grub? With the Live CD?

---

### Post by rockerphil on 2008-08-15
GRUB stands for Grand United Boot loader. it's what allows you to boot multiple OSes cleanly. but as stated earlier, Windows XP wipes the MBR thus wiping out the GRUB boot loader, but, don't be alarmed, it's not too difficult to restore the GRUB boot loader. you can find a good tuturoail on how to do this here

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

Phil

---

### Post by CheeseEatingBulldog on 2008-08-15
For easy dual boot guides (step by step with screens) goto:

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

Found that very useful.

---

### Post by zzzonked on 2008-08-15
Thanks Bulldog. I've got that bookmarked :)

---

