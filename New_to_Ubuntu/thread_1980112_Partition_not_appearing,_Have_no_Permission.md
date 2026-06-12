---
title: "Partition not appearing, Have no Permission"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by greenja1 on 2012-05-14
I'd like to add a partition that is called 410_DataStorage and have it mount at boot. I'm told I'm not the owner, so I can't change the permissions on that partition. The partition does not appear in fstab (below). Its UUID is a62b6e67-6f7e-43cf-a2c9-5264d72e5bc6.


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=da4e36ee-5bf8-418a-94eb-c95ebe1d732a /               ext4    errors=remount-ro 0       1
# /usr/local was on /dev/sda5 during installation
UUID=2dd086a6-e78d-4bfb-a947-08336d496450 /usr/local      ext4    defaults        0       2


UUID of all devices:

ls -al /dev/disk/by-uuid/
total 0
drwxr-xr-x 2 root root 180 May 11 18:29 .
drwxr-xr-x 6 root root 120 May 11 18:29 ..
lrwxrwxrwx 1 root root  10 May 11 18:30 144e8fa4-f315-4ad4-b4a7-f9106586fc55 -> ../../sda5
lrwxrwxrwx 1 root root  10 May 11 18:30 59cb5397-be31-4adc-a5df-76cd59fff1d0 -> ../../sdb6
lrwxrwxrwx 1 root root  10 May 11 18:30 6f38c55d-53e1-4972-93b5-cf0c500ea8ee -> ../../sdb5
lrwxrwxrwx 1 root root  10 May 11 18:30 8a8546e0-04cd-48d0-a937-3d9fb9e641bd -> ../../sdb7
lrwxrwxrwx 1 root root  10 May 11 18:30 a62b6e67-6f7e-43cf-a2c9-5264d72e5bc6 -> ../../sda2
lrwxrwxrwx 1 root root  10 May 11 18:30 da4e36ee-5bf8-418a-94eb-c95ebe1d732a -> ../../sda1
lrwxrwxrwx 1 root root  10 May 11 18:30 f16bfde3-b03f-4349-b380-9c05776014d6 -> ../../sdb1

---

### Post by flemur13013 on 2012-05-14
You don't say what type of partition it is: NTFS, FAT, or ext2,3,4 ?

FWIW, here's my fstab entry for an NTFS read/write partition with data and no OS:
```
UUID=whatever                       /data   ntfs-3g defaults            0 0
```Create your /data (or whatever you call your mount point), make yourself the owner and make it writable:

$ sudo mkdir /data
$ sudo chown yourname /data
$ chmod +w /data

Test it with 

$ sudo mountall
$ cd /data
$ ls -al

Edit: when you boot, does your partition show up at /mnt/410_DataStorage ?

If so, you can become the owner with 

$ chown -R yourname /mnt/410_DataStorage

then you'll own everything (-R = recursive) ; you don't need to do what I said above if you're happy with it at /mnt/410_DataStorage.

---

