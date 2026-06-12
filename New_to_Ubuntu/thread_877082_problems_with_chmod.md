---
title: "problems with chmod"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by oshilig on 2008-08-01
I'm trying to set permissions on an external hooked to a 6.06 ubuntu server edition.

I want to open this external to any and all users, for all permissions, rwx

when I try:

root@nwfco-server:~# chmod u+rwx,g+rwx,o+rwx,a+rwx /media/usbdisk/*

I get:

chmod: changing permissions of `/media/usbdisk/1': Read-only file system

for all the folders on usbdisk.

Any ideas what I'm doing wrong?  this is our organization's shared drive - so it's pretty pressing :-(

---

### Post by kestrel1 on 2008-08-01
How is the drive formatted?
You may need to chmod the drive itself, not really sure though.

---

### Post by caljohnsmith on 2008-08-01
I think you are getting that error because you aren't mounting the usbdisk as read-writable--it is mounted as read-only right now. Try doing:
```
sudo umount /media/usbdisk
sudo mount -w /dev/<usb drive> /media/usbdisk
```
If that doesn't exactly work, I think you get the idea; bottom line is you need to mount that drive as read-writable.

---

