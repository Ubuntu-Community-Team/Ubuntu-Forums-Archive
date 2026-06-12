---
title: "Booted from USB, mounting another USB"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by zaklinux on 2008-06-21
Hi All!

I successfully installed Hardy on an 8GB USB key and have been playing on it for a few weeks.

Wanted to bring is some music files from another 2GB USB key, but when I plug it into a free port, nothing happens.

The key doesn't even flash.

Any way to troubleshoot this problem?

Can I mount another USB if I'm already booting off of one?

Thanks

---

### Post by uclalinux on 2008-06-22
lsusb should list all the USB items your computer can see, 

I would, try this

```
mkdir ~/Desktop/usbtwo
```
then
```
ls /dev/ | grep sd
```
assuming that the 8Gb flash drive is sda, so it shows sda1,sda2 and sda3, for the boot, and other partitions, your second should be **sdb1** , if not there, ther should only be two sd*,(letters'), i would think that the 2Gb only has one partition so it should be sd*1, for this example lets call it sdb1,

next
```
sudo mount /dev/sdb1 ~/Desktop/usbtwo
```
now it is mounted, but lets change the own so you can  drop and drag easy
```
sudo chown <your_username>:<your_username> ~/Desktop/usbtwo   DON'T INCLUDED THE <> WHERE THE USERNAME IS, JUST PUT YOU USERNAME ie the name you sign in with
```
then there should be a folder on your desktop, if you click and open it the flash drive should be mounted there.

Post if you have problems.

---

