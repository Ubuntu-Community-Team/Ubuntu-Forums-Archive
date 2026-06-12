---
title: "Fail to move a folder in my FlashDisk, now the folder is corrupted. What should I do?"
date: 2015-10-30
forum: New to Ubuntu
---

### Post by Mikael_Pratama on 2015-10-30
In Ubuntu I tried to copy my folder from FlashDisk to Desktop. However, since my USB port is rather loose, in the middle of moving the folder my FlashDisk got dis-attached from my laptop. Ever since then, I cannot open the folder in my computer anymore. When I tried to open the folder in Windows it shows like this

[IMG]http://i.imgur.com/5rGBULE.png[/IMG]

:(

What should I do so that I got my folder back?

---

### Post by Skaperen on 2015-10-30
maybe one of those program that can recover "deleted" files?  otherwise it's toast.  how much important data do you have fewer than 3 copies of?

---

### Post by Mikael_Pratama on 2015-10-30
I have tried with TestDisk, but honestly I have no clue at all on how this problem can related to TestDisk. I am only one commit away from remote, I guess I will start over and completely forget about this :(.

---

### Post by sudodus on 2015-10-30
Welcome to the Ubuntu Forums :-)

What file system is it in the USB flashdisk? If it is a Microsoft file system, FAT32 or NTFS, you can try to repair it in Windows.

```
chkdsk -f X:
``` where X is the volume letter for the flashdisk (a Windows volume alias 'drive' corresponds to a linux partition).

If it is a linux file system, for example ext2, ext3 or ext4, you can try to repair it in linux.

```
sudo e2fsck -f /dev/sdxy
``` where x is the drive letter and y is the partition number, for example /dev/sdb1

You can also try again with ***testdisk***.

If still no luck a agree with *Skaperen*, that you can try one of those program that can recover "deleted" files. I would recommend ***photorec***, that works without a working file system as long as the file data is still there.

[www.cgsecurity.org/wiki/PhotoRec](www.cgsecurity.org/wiki/PhotoRec)

---

