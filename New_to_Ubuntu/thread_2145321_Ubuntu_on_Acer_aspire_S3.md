---
title: "Ubuntu on Acer aspire S3"
date: 2013-05-15
forum: New to Ubuntu
---

### Post by hyudryu on 2013-05-15
Hi guys, I'm trying to put Ubuntu on my aspire s3 ultrabook, but I can't seem to install it. Since I do not have a cd drive, I figured the only way to install it is via USB. 

I followed this guide: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

But when I boot up my laptop and press F12, I can't choose the USB to boot from.

[IMG]http://img11.imageshack.us/img11/3852/lgta8cd.png[/IMG]

How can I enable USB so that I can install from there? I've been trying for a while but I can't seem to get it haha.

---

### Post by moody_mark on 2013-05-15
Perhaps that machine has UEFI firmware, is it a Win8 machine normally? You might need to turn off secure boot in the BIOS: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by hyudryu on 2013-05-15
No it's not windows 8. it's stock windows 7

I installed "ubuntu-12.10-server-amd64" onto my usb using Universal USB Installer and it looks like this
[IMG]http://img856.imageshack.us/img856/9606/lgtddc5.png[/IMG]

I'll try turning off secure boot and see what happens. Thanks :)


[B]EDIT:
[/B]I just enabled to boot from USB and everything works fine, but when I'm partitioning to install alongside with windows 7, I chose 25gb partition space and it's taking a long time. Wonder if it's normal....

---

### Post by moody_mark on 2013-05-16
Good to hear its working, the 25GB partition im assuming is for Ubuntu, should be enough. Yes the partitioner may well take some time, as it will have to shrink the windows partition to make room for your new one. Just be patient and let it do its thing, have a cup of tea or two whatever you do dont stop a disc partition action part way through or you could do some damage.

---

