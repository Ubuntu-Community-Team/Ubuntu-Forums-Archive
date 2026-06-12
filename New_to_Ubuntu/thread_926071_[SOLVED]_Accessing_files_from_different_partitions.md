---
title: "[SOLVED] Accessing files from different partitions"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by WindowsWeenie on 2008-09-21
I installed Ubuntu with Wubi and dual boot with XP. Within Ubuntu I can access files stored on the XP partition. Is there any way to access files in the Ubuntu partition while in XP?

Also I've been having problems with media players as discussed [here]("http://entitledtoanopinion.wordpress.com/2008/09/05/cursed-technology/").

---

### Post by unutbu on 2008-09-21
The ext2ifs driver will allow you to read and write to your Ubuntu ext3 filesystem from Windows. See [http://www.fs-driver.org/](http://www.fs-driver.org/)

Although it may not be clear from reading the homepage, the FAQ ([http://www.fs-driver.org/faq.html](http://www.fs-driver.org/faq.html)) states that among the features supported is:
> 
Complete reading and writing access to files and directories of volumes with the Ext2 or Ext3 file system.

---

### Post by MasterNetra on 2008-09-21
Really? I thought you had to transfer files to and from a Fat32 partition? Well thats one method at least anyway :P Sense both Ubuntu & Windows by default the only Partition type both share in recognition is Fat32. But if that driver thing works then by all means use it. Sense setting up a FAT32 partition can be a bit of a pain and wastes space that could otherwise go to either of your OS's.

---

### Post by egalvan on 2008-09-21
> **MasterNetra said:**
> Really? I thought you had to transfer files to and from a Fat32 partition? Well thats one method at least anyway :P Sense both Ubuntu & Windows by default the only Partition type both share in recognition is Fat32. Sense setting up a FAT32 partition can be a bit of a pain and wastes space that could otherwise go to either of your OS's.

Ubuntu Hardy supports NTFS out-of-the-box.

FATx is much too limiting.

---

### Post by Bucky Ball on 2008-09-21
As this is a wubi install, wouldn't that mean wubi is on a virtual partition within windoze? How would windoze access Ubuntu files? Not sure what filetype that partition is as not that experienced with wubi. (Installed for a demo for awhile on a friend's machine and worked great but haven't checked the subtleties yet).

---

### Post by unutbu on 2008-09-21
Thanks Bucky Ball, I forgot the OP said he was using Wubi.
So it seems my first suggestion was wrong. ext2ifs may not be useful to the OP.
I don't know much about Wubi, but according to this thread:

[http://ubuntuforums.org/showthread.php?t=814477](http://ubuntuforums.org/showthread.php?t=814477) 

The explore2fs app can read the Wubi filesystem-in-a-file (loop mounted device) from within Windows: [http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

---

### Post by WindowsWeenie on 2008-09-21
ex2ifs didn't work. I just downloaded explore2fs but I can't find any img file. I discovered I could access my Windows partition in Ubuntu by doing a file search, but doing the same thing in Windows doesn't work. I don't know where to look to find the files in the other partition.

---

### Post by unutbu on 2008-09-21
According to [https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?) Wubi files are located at C:\ubuntu\disks.

---

### Post by WindowsWeenie on 2008-09-21
Thanks, it works fine.

---

### Post by Bucky Ball on 2008-09-22
Good news. \\:D/

Don't forget to mark your thread as solved using Thread Tools so others can surf here to try and fix their problem. If you have other issues, post in a new thread as you will have a better chance of getting help with the correct issue outlined in your thread title.

Enjoy your explorations.

---

