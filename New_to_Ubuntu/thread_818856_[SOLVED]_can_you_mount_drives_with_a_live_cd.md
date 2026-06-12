---
title: "[SOLVED] can you mount drives with a live cd?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by slymi2005 on 2008-06-04
I'm trying to mount my hd using a livecd but I am having trouble doing so. The reason I want to do this is because only through the live cd (kubuntu 7.10) does the computer recognize my sony walkman when it is connected through the usb port. So basically if I could get to the files that are on the ubuntu 8.04 install I would be able to load my mp3 player. Thank you in advance.

---

### Post by Joeb454 on 2008-06-04
I think you can yes. Check the "Places" menu. It may be listed in there, if not choose Places > Computer and mount it from there :)

---

### Post by slymi2005 on 2008-06-04
I probably should have mentioned this in the first post, sorry. The computer does recognize my two partitions but it doesn't allow me to mount them, it tells me "hal-storage-fixed-mount refused uid 999" I have no idea what that means.

---

### Post by Joeb454 on 2008-06-04
can you post the output of ```
sudo fdisk -l
``` note - that is a lowercase 'L' :)

Also how big is the partition you are trying to mount? And don't forget to use [CODE] tags :)

---

### Post by slymi2005 on 2008-06-04
```
Disk /dev/sda: 20.0 GB, 20020396544 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001da31

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         893     7172991   83  Linux
/dev/sda2             894        2434    12378082+  83  Linux

```

one is 12 gb and the other is 7.3 gb the total is about 20

---

### Post by Joeb454 on 2008-06-04
What happens if you open a terminal and run ```
sudo mkdir /media/HDD1
sudo mount /dev/sda1 /media/HDD1
``` I *think* that's the right syntax ;)

---

### Post by slymi2005 on 2008-06-04
> ubuntu@ubuntu:~$ sudo mkdir /media/HDD1
mkdir: cannot create directory `/media/HDD1': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/HDD1
mount: /dev/sda1 already mounted or /media/HDD1 busy
mount: according to mtab, /dev/sda1 is already mounted on /media/HDD1

It works now, thanks. So what part should I do every time I want to mount it or will it automount now?

---

### Post by Joeb454 on 2008-06-04
I think you would have to do it every time you boot from the live CD. I think you have to edit /etc/fstab to automount, though I've never done it myself :)

---

### Post by slymi2005 on 2008-06-04
Thank you so much you've been so helpful.

---

### Post by Joeb454 on 2008-06-04
Not a problem :)

---

