---
title: "Changing permissions of subfolders in a mounted FAT32 partition"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by sharad.sharma on 2008-08-04
I just setup a dual boot with Ubuntu 8.04 and WindowsXP. To mount 4 FAT32 partitions at startup, I made entries in fstab.The file fstab now looks like :
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=5ba8d17a-cd81-4f3f-bcdf-b9fc479f6b71 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=489c3188-6c51-433b-b000-1a04e4f3d5ee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


/dev/sda1 /media/C vfat umask=0000 0 0 
/dev/sda5 /media/D vfat umask=0000 0 0 
/dev/sda6 /media/E vfat umask=0000 0 0 
/dev/sda7 /media/F vfat umask=0000 0 0 
```

Now there are some directories in these 4 FAT32 partitions which are locked.A lock emblem appears on those folders.I can not write in those folders.I can't change the permissions either.It says that only the owner(root) can.What should I do? Please help

Thank you

---

### Post by drs305 on 2008-08-04
Change your vfat entries to look like this:
```

/dev/sda**X** /media/**X** vfat  users,uid=1000,gid=1000,umask=022 0 0


```

The gid and uid make you and your group the owner. Ownership of vfat and ntfs partitions is created at mounting and don't change until unmounted. The above command will make user=1000 the owner.

---

### Post by cdtech on 2008-08-04
I'm too slow, lol.

I was going to say about the same thing.........

```
/dev/sda1 /media/C vfat defaults,umask=002,gid=46
```

---

### Post by sharad.sharma on 2008-08-04
Thanks drs305 and cdtech! Changed the fstab entries and then modified the permissions of the 4 directories :)

---

### Post by cdtech on 2008-08-04
cool.......:)

---

