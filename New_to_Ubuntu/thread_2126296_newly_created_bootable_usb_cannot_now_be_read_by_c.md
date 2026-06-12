---
title: "newly created bootable usb cannot now be read by computer"
date: 2013-03-16
forum: New to Ubuntu
---

### Post by temujin99 on 2013-03-16
Hello
I have a mac ibook G4 - OS is 10.4.11.
I believe, I think, following the instructions to convert .iso to .img.dmg, I successfully created a bootable USB. 

However when I restarted the computer holding down the alt key, the notice said that the disk is "not readable by this computer".

In disk utilities I recognise the disk named 'disk1s1' - containing circa 753 MB - as the disk referred to when I do the steps in Terminal. (Disk 1 is the 4GB USB (with other stuff on it)). 

What have I done wrong and what can I do to correct my mistake. Please!

Thanks

Gordon
Any answers in language for dummies if you don't mind.

---

### Post by sudodus on 2013-03-16
Download the proper iso file! There are different architectures for intel/amd PC and powerpc.

Check that it was properly downloaded with md5sum and the list at[URL="https://help.ubuntu.com/community/UbuntuHashes"]
https://help.ubuntu.com/community/UbuntuHashes[/URL]

I can help you to create an Ubuntu install USB drive with Unetbootin from linux or Windows. Format a partition on the USB drive with FAT32. Install/Run Unetbootin to create the USB install drive.

But if you have only the ibook, you have to wait for someone else to help you create it.

---

### Post by temujin99 on 2013-03-16
Thank you for this. Maybe I have downloaded the wrong iso. I'll go back.

I only have my ibook - powerpc

---

