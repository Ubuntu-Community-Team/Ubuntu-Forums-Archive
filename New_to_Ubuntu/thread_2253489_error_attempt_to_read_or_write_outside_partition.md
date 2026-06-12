---
title: "error: attempt to read or write outside partition"
date: 2014-11-20
forum: New to Ubuntu
---

### Post by viv5 on 2014-11-20
Looks like I did some error while partitioning. 
Went through most of the forum threads but still am not able to boot.

I am getting the following error

error: attempt to read or write outside partition
entering rescue mode
grub rescue>

I ran the following commands

grub rescue> ls
(hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)

grub rescue> ls (hd0,1)/
./ ../ lost+found/ect/media/bin/boot/dev/home....var/vmlinuz initrd.img cdrom/

Can anyone tell me how to proceed. I am running Ubuntu on Virtual Box?

---

### Post by bashiergui on 2014-11-22
Was this a new installation inside of virtualbox? Or did you try to change the partition table after installation? What are you trying to accomplish in the virtual machine?

---

