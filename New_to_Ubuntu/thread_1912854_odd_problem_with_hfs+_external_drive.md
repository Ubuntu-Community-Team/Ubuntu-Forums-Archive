---
title: "odd problem with hfs+ external drive"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by 118118 on 2012-01-21
when i plug it in it auto mounts but as read only. i try to force it to remount with

```
sudo mount -t hfsplus -o remount,force rw /media/Backup

```i get the message 

```
sudo mount -t hfsplus -o remount,force rw /media/Backup

```
if i then plug it into my macbook and check that it's not journaled with the "mount" command in the mac terminal, it says no it isn't: but then after ejecting it from the mac it will automount in ubuntu as read and write. but i have to do this each time i remove the drive from the ubuntu machine!

thanks :popcorn::popcorn:

---

### Post by Double.J on 2012-01-21
Hi there, sorry are you using two different machines, or dual booting on the mac? If it's dual booting, I'd suggest making an entry in the fstab?

Have a look at [Drowsyhase's thread]("http://ubuntuforums.org/showthread.php?t=1723857") on the subject - this has been working for me with journalling enabled, though I understand that doing this for the OS X primary is a bad idea?

Hope it helps! All the best

---

### Post by 118118 on 2012-01-21
two machines, sorry.

---

