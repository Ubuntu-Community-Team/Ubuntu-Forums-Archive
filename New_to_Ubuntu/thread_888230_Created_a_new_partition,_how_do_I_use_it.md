---
title: "Created a new partition, how do I use it?"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by burtzacarach on 2008-08-12
I used gparted to make a 15GB ext3 partition that I planned on using to store my music on but I'm not entirely sure how to access it.

How do I download to my new partition?

---

### Post by sandysandy on 2008-08-12
u can find ur new partition under  Places----> Computer

regards

---

### Post by glennric on 2008-08-12
You have to mount it.  Make a mount point for it.  For instance
```
sudo mkdir /mnt/new
```
(Change "new" to whatever you want.  In fact you can make the mount point somewhere else if you like - perhaps in /media or in your home directory)
Then type
```
sudo mount /dev/???
```
where ??? is the device name of the partition.  Type "sudo fdisk -l" for a list of partitions available on your system.
Then you can access it.  To mount it automatically you will have to add a line in the file /etc/fstab.

---

### Post by burtzacarach on 2008-08-12
I created a mount point at
/mnt/music

and when I tried to mount it with
mount /dev/sda3

terminal returned
can't find /dev/sda3 in /etc/fstab or /etc/mtab

btw: i'm running hardy with the Xfce desktop environment i'm not sure if that makes any difference but now ya know

---

