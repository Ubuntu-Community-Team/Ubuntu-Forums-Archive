---
title: "can't resize ntfs partition due to bad sector"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by bjameswilliams on 2008-04-24
i've defragged & run chkdsk from windows xp & all that but gparted still won't let me resize the ntfs partition because it recognizes a 'bad sector.'

i tried running 'ntfsresize' from command line with the '-b' option to accommodate the bad sector but it told me i needed to "specify exactly one device."

what do i need to do? how do i specify the device, which i assume is the hard drive?

---

### Post by dark_harmonics on 2008-05-21
Hi and welcome to the community. Bad sectors are never a good thing. Remember that it is best to defragment the partition before resizing it to ensure no data gets clipped. You will also want to backup any data before doing ANYTHING to your partition. 

To find out the device name of your ntfs drive you will need to type sudo fdisk -l. you will see one of the entries like /dev/hda or /dev/sda or something similar that has an NTFS partition. That is likely to be your drive.

---

### Post by TitanTiger on 2008-05-21
I was having this same problem even after replacing the drive (the first actaully did have bad sectors and was under warranty).  What worked for me was installing Ubuntu without partitioning (in other words, erasing the Windows install altogether.  Then I restored my Windows image (wiping out Ubuntu) and went back through the Ubuntu install and partitioned the drive.  Everything worked like it was supposed to then.

Obviously you'll need to make a bootable disc image of your Windows install using a cloning program like Norton Ghost or DriveClone (my choice) before doing this.  Mine only took up a couple of DVDs.

It's worth a try.  I have no idea why it took that to work for me, but it did.

---

