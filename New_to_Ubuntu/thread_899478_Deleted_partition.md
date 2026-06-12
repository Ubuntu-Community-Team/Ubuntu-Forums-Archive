---
title: "Deleted partition"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by AngryNapkin on 2008-08-24
I inadvertently deleted an NTFS windows partition from ubuntu. I haven't created a new partition over that space, it still says unallocated space. Is there any way I can get those files back?

---

### Post by Elfy on 2008-08-24
Not usre if this will help much, but you might be able to get at them with photorec or testdisk, both are avilable through the repos.

The most important thing to do at the moment is stop using the harddrive at all - reboot with the livecd. 

You can access the net and also download testdisk from there to try and recover.

---

### Post by AngryNapkin on 2008-08-24
Thanks, Do I need to create a partition over it though? Will testdisk see aynthing there except unallocated space?

---

### Post by Catalyst2Death on 2008-08-24
Usually when you delete a partition, you delete the entry from the partition table, making it possible for a formatting program to write a new entry to the partition table and begin to write data to that area of the disc.  If all you did was delete the partition, then all you did was remove the partition table.  All of you data should still be there.  This way if you run a program that can read the disc and regenerate the partition table from it, then you should in theory restore your partition.  This is my understanding of how these processes work, if I'm incorrect someone please correct me.

Edit: To answer your question: Do *NOT* create a partition over the old one, it will erase all of you data.

---

### Post by Elfy on 2008-08-24
> To answer your question: Do *NOT* create a partition over the old one, it will erase all of you data.
+1

I'm sure that is the case - and testdisk says it can 

> Fix partition table, recover deleted partition

Boot the livecd - search the forums for recover partition table or something similar, use uboontu.com 

You should be able to install it with 

```
sudo apt-get install testdisk
``` if it doesn't install it's only the repos need sorting.

---

### Post by melrokz on 2008-08-24
Use Acronis Disk director 10 boot cd for a proper GUI program for restoring NTFS and FAT partitions that have been deleted by mistake. You have to do this as soon as possible.

---

