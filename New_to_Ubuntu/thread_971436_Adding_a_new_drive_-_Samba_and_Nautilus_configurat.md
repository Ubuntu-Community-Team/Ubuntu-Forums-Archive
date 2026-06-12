---
title: "Adding a new drive - Samba and Nautilus configuration issue"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by treaney on 2008-11-05
I have added a 750 GB drive as /hdb to my Ubuntu 8.1 system which has a 160 GB fitted.

I'm using SAMBA to access files on the 160GB drive sucessfully.

I have sucessfully mounted the 750GB but have had problems setting file permissions using chown. I ended up using sudo nautlis to setup the file shares but this has to be redone each time server is rebooted.

I thought I could do it with SAMBA but the 750GB drive does not appear in the /Places/Computer/Home Folder as the 160GB drive does. The 750GB drive does appear in /Places/Computer though.

What am I missing?



1. Erased partitioning on the drive using parted(previously had NTFS partitioning)
2. Formated the drive to EXT3 using fdisk
3.Tried to change fstab by adding
/dev/hdb	/shared	 ext3	rw	 0	0

---

