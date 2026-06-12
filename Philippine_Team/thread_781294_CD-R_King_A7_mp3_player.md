---
title: "CD-R King A7 mp3 player"
date: 2008-05-04
forum: Philippine Team
---

### Post by kstella on 2008-05-04
Hey, guys. Napanalunan ko 'to sa isang raffle. Kaso, hindi siya nadedetect ng PC ko. Etong manual: [http://www.cdrking.com/download/mp3/mp3_a7/a7.htm](http://www.cdrking.com/download/mp3/mp3_a7/a7.htm). Mukhang gawa ito para sa Windows users, but when has that stopped us before? ;p

Sa tingin ko, baka kulang ng Linux driver, o baka kailangan kong i-mount nang manwal. Kaso, hindi ako marunong mag manual mount, hehe. Any ideas?

Salamat.

---

### Post by tech0007 on 2008-05-04
Try mo:

sudo mount -t vfat -o rw /dev/sdX /media

X = from a-z yan depende sa kung ilan hdd, cdrom, usb devices mo. sakin sdc.

---

### Post by raxso on 2008-05-04
to check kung san device/partition

sudo fdisk -l

---

