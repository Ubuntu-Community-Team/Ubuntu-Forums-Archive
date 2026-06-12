---
title: "mount volume"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by mr2v6 on 2008-09-23
Hi,
I have a windows xp box that has a shared hard drive.  It is connected to another Linux box via usb.  

Everytime I log in to ubuntu I have to map the drive manually.  Is there a way in Ubuntu to fix this, or is the problem on the side of the windows xp box?

thanks,
MR2V6

---

### Post by jken146 on 2008-09-23
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by acidsolution on 2008-09-23
have the entry in 

/etc/fstab

and than 

sudo mount -a

---

