---
title: "How to mount and read files from EXT3 Ubuntu partition on Windows 10?"
date: 2019-10-12
forum: New to Ubuntu
---

### Post by ranice on 2019-10-12
I have tried using Ext2 Volume Manager as an administrator. When I try to mount the partition, the partition is mounted however I am still unable to access the files unless I format the partition, and I get an error saying:
[INDENT]F:\ is not accessible. The volume does not contain a recognised file system.
[/INDENT]I also tried using Ext2explore (run as administrator) however I am unable to read the files as nothing shows up even after repeatedly scanning my hard disk.

Is there any other recommended software that can use to read files from my ubuntu partition?

This is what I am seeing when I use ext2 volume manager. The partition I want to mount is the ext3 partition with 39GB.


[ATTACH=CONFIG]284177[/ATTACH]

Thank you all in advance for the responses!

---

### Post by SeijiSensei on 2019-10-12
I'd mount that big NTFS partition in Ubuntu and copy over the files you want to access from Windows.  Surely you don't need to read the contents of /usr or /var, right?

---

### Post by Holger_Gehrke on 2019-10-12
Is [ext2fsd]("https://sourceforge.net/projects/ext2fsd/") what you're using ? That seems to have a problem with the 64-bit feature of ext4 filesystems. You can use 'resize2fs -s'  to turn that feature off.

Holger

---

### Post by ranice on 2019-10-14
I just wanted to transfer a large chunk of homework from ubuntu to windows because LibreOffice is terrible at editing documents... in the end I just transferred using a thumb drive haha

---

