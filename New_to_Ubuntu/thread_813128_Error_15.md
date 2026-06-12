---
title: "Error 15"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by Danthedunce on 2008-05-30
Help, please.

I'm new to Ubunto and of limited computer literacy, hence the name.   I have loaded Ubuntu but when I try to run it I receive the following:

Filesystem type is ntfs, partition type 0x7 
kernel /boot/vmlinuz-2.6.24 - generic root = UUID = 8AECFA00ECF9E67B loop = / ubuntu/disks/root.disk ro quiet splash

Error 15:  File not found

Can someone please get me out of this mess using a simple explanation.  I also suffer from 'senior moments'.  Thanks

---

### Post by Duck2006 on 2008-05-30
> Filesystem type is ntfs, partition type 0x7
kernel /boot/vmlinuz-2.6.24 - generic root = UUID = 8AECFA00ECF9E67B loop = / ubuntu/disks/root.disk ro quiet splash

Some thing seems wrong here. Try reinstalling ubuntu again and use this link.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Jackie999 on 2008-05-30
This post [http://ubuntuforums.org/showthread.php?p=4846453](http://ubuntuforums.org/showthread.php?p=4846453) seems to cover the same error with a solution...maybe it will help

---

### Post by bumanie on 2008-05-30
Sounds as though you have installed to a partition formatted with ntfs. This is the windows filesystem, linux uses ext 3. Linux can reas/write to ntfs, but needs the system files to be on a native format. Install again, but at the partitioning stage, choose ext3 when you format the partition, ubuntu is to be installed to.

---

