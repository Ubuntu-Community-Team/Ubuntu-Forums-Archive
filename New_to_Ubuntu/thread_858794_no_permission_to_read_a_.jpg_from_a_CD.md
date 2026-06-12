---
title: "no permission to read a .jpg from a CD?"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by ozzyprv on 2008-07-13
I am trying to copy some pictures from a CD to a local folder on my HD.

I keep getting the following message when I try:
> "/media/cdr...c06654.jpg" cannot be copied because you do not have permissions to read it.

Attached is an screen shot of the files I am trying to copy.

Any help? 

Thanks.

---

### Post by ChameleonDave on 2008-07-14
Please open a terminal and do this:

```

cat /etc/fstab
sudo blkid

```

Post the output here.

---

### Post by ozzyprv on 2008-07-15
This is what I got:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=c2dbb188-73df-4b27-9809-eb8efe18f22d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb3
UUID=58fd8937-aa70-42ca-8c60-ccaf066b3c9f /home           ext3    defaults        0       2
# /dev/sda1
UUID=90E840C6E840ABF2 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=46C9-1DE8  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdb4
UUID=b7ad4a74-c2b3-4878-8c20-2d91fbd63372 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
#Shared files

me@Ubuntu:~$ sudo blkid
[sudo] password for me: 
/dev/sda1: UUID="90E840C6E840ABF2" LABEL="C Mfixed" TYPE="ntfs" 
/dev/sdb1: UUID="46C9-1DE8" TYPE="vfat" 
/dev/sdb2: UUID="c2dbb188-73df-4b27-9809-eb8efe18f22d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: UUID="58fd8937-aa70-42ca-8c60-ccaf066b3c9f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb4: TYPE="swap" UUID="b7ad4a74-c2b3-4878-8c20-2d91fbd63372" 
```

---

### Post by shadow-of-sin on 2008-07-15
Does this problem occur for all CDs or just this particular one?

If you want to copy the files you can do so by running nautilus as root:
```
gksudo nautilus
```

---

### Post by ozzyprv on 2008-07-15
First time that I remember seeing this error message.

---

