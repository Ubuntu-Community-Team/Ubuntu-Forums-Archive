---
title: "[SOLVED] Problems with permission in external HDD"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by Berean on 2008-06-06
Hi,

I've got a Seagate 250 GB ext HDD, partitioned to 84GB (ext 3) and 154GB (Fat32 or possibly Fat 16).  Using Grsync to backup up my internal documents I can't gain permission to copy to ext 3, but have no problems with sync-ing to Fat 32 partition.  Even when I attempt to simply copy files to ext 3 it continues to say I don't have permission.  I've read about this in my Ubuntu book, but I'm becoming increasingly confused.  Any help much appreciated.  Regards,

---

### Post by sisco311 on 2008-06-06
You need to change the owner of the partition:
```
sudo chown -R $USERNAME. **/media/disk-X**
```assuming the partition is mounted in the */media/disk-X* directory.
Read more about permissions: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Berean on 2008-06-06
Thanks,

I've tried what you suggested but got the following;
chown: missing operand after `./media/disk'

Any ideas?

PS When I look in properties of the disk and then permissions, it states that the permissions of the "disk" could not be determined.

---

### Post by sisco311 on 2008-06-06
EDIT: first post the output from
```
mount
```

It's a space after $USERNAME.
sudo chown -R $USERNAME.**       /media/disk**

---

### Post by Berean on 2008-06-06
Sisco311,

I've been looking over my books - and the link you gave me - and I've managed to sort it.  Many thanks for your help.  Regards,

---

### Post by mctk on 2008-06-22
Thanks for the tip, sisco311, I had the same issue. Now that I totally chown my second hard drive, nautilus and others can write files there.  That's nice.  However, when I click properties, it still says that the permissions could not be determined.  It's an ext3 partition, which has no errors according to fsck.  Doesn't seem like a problem, but somethings misconfigured somewhere.  Currently seems like only a minor annoyance.

---

