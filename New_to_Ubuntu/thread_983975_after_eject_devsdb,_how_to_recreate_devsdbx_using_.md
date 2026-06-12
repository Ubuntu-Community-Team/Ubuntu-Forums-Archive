---
title: "after eject /dev/sdb, how to recreate /dev/sdbx using command"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by say2sky on 2008-11-16
here /dev/sdb is a usb external hdd

after using eject /dev/sdb,  /dev/sdbx for each partition will gone.

how I can recreate /dev/sdbx for every partition by using command line.

now I can unplug usb external hdd and plug in it again but I hope to use command line to achieve the same thing.

---

### Post by Moop on 2008-11-16
The command for unmounting a device is umount. You can unmount partitions by specifying the partition. An example would be ```
umount /dev/sde1
```

---

### Post by say2sky on 2008-11-16
> **Moop said:**
> The command for unmounting a device is umount. You can unmount partitions by specifying the partition. An example would be ```
umount /dev/sde1
```

thanks for help.

I know umount can be used to unmount a partition and remount it again.

I also curious if there is a opposite command after using eject /dev/sdb

---

### Post by say2sky on 2008-11-16
sometimes when there are many partitions on one hdd, I just use eject /dev/sdb to unmount all partitions,

on that situation, if there are any method to mount partition again?

---

