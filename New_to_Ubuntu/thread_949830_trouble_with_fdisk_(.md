---
title: "trouble with fdisk :("
date: 2008-10-16
forum: New to Ubuntu
---

### Post by zamadatix on 2008-10-16
i'm running through a  tutorial for a persistent install of xubuntu 8.04 onto a usb drive from ubuntu ([http://www.pendrivelinux.com/2008/05/21/usb-xubuntu-804-persistent-install-from-linux/]("http://www.pendrivelinux.com/2008/05/21/usb-xubuntu-804-persistent-install-from-linux/")) but am having a small problem with fdisk -l. whneveri run it this happens:
daniel@ubuntu:~$ fdisk -l
daniel@ubuntu:~$ 

any ideas?

---

### Post by zamadatix on 2008-10-16
was i supposed to add a mount point in gparted?

---

### Post by fooman on 2008-10-16
did you try:

```
sudo fdisk -l
```

---

### Post by zamadatix on 2008-10-16
wow im retarded lol :oops:, thanks alot!

---

### Post by zamadatix on 2008-10-16
well while this thread is here i mine as well get help with this one... same tutorial... next step...

im trying to do **syslinux -sf /dev/sdf1** but it sai permission denied or something, so i tried **sudo syslinux -sf /dev/sdf1** but wasn't even prompted for the sudo password, lets see what was so obvious this time ;)

---

### Post by fooman on 2008-10-16
if you followed the last sudo command by only a few minutes....then it won't prompt you for the password again.  i am not sure how long that grace period lasts (5 minutes?)...but  by default, it gives you that little bit of time before prompting you again.

---

### Post by zamadatix on 2008-10-16
oh i never knew that :P. if i do the syslinux thing data doesn't go on the actual drive right?

---

### Post by zamadatix on 2008-10-16
i decided to make the 2nd partition on my usb from grub wich apparenlt doesnt work :/ so i deleted the second partition and type in what the site told me to: **mkfs.ext2 -b 4096 -L casper-rw /dev/sdb2**but i get the error:
[B]daniel@ubuntu:~$ mkfs.ext2 -b 4096 -L casper-rw /dev/sdb2
mke2fs 1.40.8 (13-Mar-2008)
Could not stat /dev/sdb2 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
daniel@ubuntu:~$ 
[/B]

last time i used gparted sdb went to sdf but i checked again in gparted after a 6th 5 minute wait to load my entire hard drive THEN my usb... and im still sdb

---

