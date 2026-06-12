---
title: "How to Mount Usb Drives in Terminal"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by overcyn on 2008-04-28
Just installed ubuntu 2 days ago and i have this external usb hd and i can mount and unmount it by right clicking and selecting Mount Volume or Unmount Volume. But..... i want to learn to use the terminal. So far, i have figured out to unmount i need to type

sudo umount /media/Storage

where Storage is the name of the external hd. This works. but when i try to mount by typing 

sudo mount /media/Storage 

i get this error 

mount: can't find /media/Storage in /etc/fstab or /etc/mtab

even though theres an icon in /media named Storage which i can mount by right clicking. where am i going wrong? thanks in advance

:guitar:

---

### Post by gunbladeiv on 2008-04-28
have you read the manual for mount?
anyway the /media/storage is the mount point and it's not the source.
Suppose, you need to check /dev/ for your USB device.

If your external hdd located at /dev/sda# (which # is number) .. then to mount it, you need to:```
sudo mount /dev/sda# /media/storage
```

The syntax is simple:
```
sudo mount <source location> <mount point folder/destination>
```

I hope this will help

---

### Post by SOULRiDER on 2008-04-28
If its not in your /etc/fstab file you will need to use the device name isntead of /media/Storage.

Its probably called something like sdb1. Devices are always under /dev/ so you can try mounting /dev/sdb1. To see all discs and aprtitions try doing
```
ls /dev/ | grep /sd
```

---

