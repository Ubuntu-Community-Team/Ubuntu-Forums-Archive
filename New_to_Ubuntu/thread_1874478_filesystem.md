---
title: "filesystem"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by mallesh453 on 2011-11-03
how can i change removable disk permissions?
i mean should i use /dev/sdb1,2,5 or /media/disk or some other thing.
and what is the relation between /dev/sdb1,2,5 and /media/disk?

actually, i need to give read only/write only permissions to attached usb mass storage device.
any help??????????????????

---

### Post by Paqman on 2011-11-03
The stuff at /dev is the actual device. Everything in Linux is represented as a file, and that includes devices like hard drives, USB sticks, CD drives, RAM, etc, etc.

When the system mounts some storage, it shows up in /dev, but the actual filesystem on that device will show up mounted somewhere else, such as /, /home, or /media. /media is the default location for any removable storage you insert.

If you want to change the permissions for files on a device, you'd change them in the location it's actually mounted to ie: /media/something. Note that not all filesystems support Linux permissions. Many removable devices are formatted as FAT32, which is an old Microsoft filesystem.

---

### Post by mallesh453 on 2011-11-03
thank you for ur reply. i got some idea now.
//Note that not all filesystems support Linux permissions.
i observed this one.

---

### Post by mallesh453 on 2011-11-03
thank you for ur reply. i got some idea now.
//Note that not all filesystems support Linux permissions.
i observed this one.
actually, i need to give read/write only permissions to usb mass storage device.
any help???????????

---

### Post by blackbird34 on 2011-11-03
Well if you're talking about read/write permissions, you're talking about linux permissions, so i'd say ext4. But Windows wont support that. Have you had a look in the 
Ubuntu Help:
[https://help.ubuntu.com/](https://help.ubuntu.com/)
or the Ubuntu Wiki
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)
 ?

---

### Post by Carborundum on 2011-11-03
If you want full read/write permissions on a FAT-system, you need to set yourself as the owner when you mount it (otherwise the owner defaults to root, and you have to sudo everything). You can do this by adding the option uid=USERNAME to the mount command, where USERNAME is your username.

---

