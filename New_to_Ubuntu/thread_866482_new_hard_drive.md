---
title: "new hard drive"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by erivera6 on 2008-07-21
Hello All,
   I recently had to replace a hard drive in a computer with 2 hard drives:

/dev/hda0
/dev/hda1

hda0 is the one I replaced. hda1 is my /storage folder, already formatted ext3.

Once I re-install Ubuntu, will it automatically recognize it and mount it? Or do I just have to edit fstab?

---

### Post by logos34 on 2008-07-21
It should see it.

If not, [follow this guide]("http://www.psychocats.net/ubuntu/mountlinux") to create mount point and add to fstab.

To use 'UUID=' format, find with 

sudo blkid

---

### Post by Rolcol on 2008-07-21
Wait...  That looks like it's the same hard drive with 2 partitions (0 and 1).  If it's a second drive it should be hd**b** instead of hd**a**.

---

### Post by erivera6 on 2008-07-21
oops...
   sorry, I did mean /hda and /hdb.

However, I want to dual boot the system, and have NTFS and ext3 storage on /hdb.

Thanks for all your help.

Ernesto

---

