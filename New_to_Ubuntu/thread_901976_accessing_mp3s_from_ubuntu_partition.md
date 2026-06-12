---
title: "accessing mp3s from ubuntu partition"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by KeithF40 on 2008-08-26
I have ubuntu on the first partition and xubuntu on the third, as the swap drive is on the second.  I uploaded all my mp3s from my windows machine to the ubuntu drive, how can I access them from the xubuntu partition?

---

### Post by halitech on 2008-08-26
you should be able to mount the drive where you have them

open a terminal and do
```
sudo fdisk -l
``` and post the info back here

---

### Post by KeithF40 on 2008-08-26
/dev/sda1-linux(this is the boot drive apparently and im in xubuntu right now but i installed ubuntu on sda1 so not really sure)
/dev/sda2-swap
/dev/sda3-linux
/dev/sda4-windows

---

### Post by -Zeus- on 2008-08-26
post the output of ```
df
```

---

### Post by KeithF40 on 2008-08-26
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             19380708   2595640  15808316  15% /
varrun                  777796       104    777692   1% /var/run
varlock                 777796         0    777796   0% /var/lock
udev                    777796        52    777744   1% /dev
devshm                  777796         0    777796   0% /dev/shm
lrm                     777796     39760    738036   6% /lib/modules/2.6.24-19-generic/volatile

---

### Post by nicedude on 2008-08-26
So if you are on sda1 as boot and want to mount sda3 to get at your files you would do the following supposing that you are using sda1 and want to mount sda3 and that sda3 has a filesystem type of ext3 as most linux do.

mkdir /media/myfiles
sudo mount -t ext3 /dev/sda3 /media/myfiles

and that should work or reverse it if you are on sda3 and want ot mount sda1 etc.

So if other way around then it would be like the following as all you would have to change is to change the partition number

mkdir /media/myfiles
sudo mount -t ext3 /dev/sda1 /media/myfiles


Hope this helps out

---

### Post by crispy_420 on 2008-08-27
Not really relevant to your question but I have to ask:

Why Ubuntu and Xubuntu both installed? Why not just install both desktops on one install? Then you can have a whole partition for music.

Sorry, had to ask.

---

