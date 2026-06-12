---
title: "Backup USB"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by ChrisB111 on 2008-11-24
I have a usb stick running Ubuntu, I want to backup the whole thing to a hard drive. I tried creating an image of the usb drive but this seamed to mess with the drive as it didn't start up properly after. Is there a right way to do this?

Thanks,

Chris

---

### Post by jbrown96 on 2008-11-24
the best way is to make an image. Find out which device it is (i.e /dev/sda, /dev/sdb, etc) with fdisk 
```
sudo fdisk -l
``` You should be able to locate it by size.

Now you can copy it with ```
sudo dd if=/dev/sdX of=/BACKUP/LOCATION/BACKUP.IMG
``` Change the X to your device and the location to whatever you want. You don't need an extension (.img) but it may help to remember what it is. To restore the device simply swap the if= and of= locations

---

### Post by ChrisB111 on 2008-11-24
Is it possible to do this while running the USB Stick because I only have windows on my PC?

---

### Post by jbrown96 on 2008-11-26
Good question. I'm not sure. It won't cause any damage, though. I believe that you can't access block devices when they are mounted, so it wouldn't work. It's worth a try though.

The reason I suggested the dd command is because it will copy the partition table and mbr, which makes restoring the system much easier. You could just backup all the files, but this won't work if the partitions/mbr change on the USB stick.

```
sudo cp -R / /BACKUP/LOCATION
```

---

