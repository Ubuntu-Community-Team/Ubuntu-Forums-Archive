---
title: "ubuntu and ebook in the read only mode"
date: 2017-04-28
forum: New to Ubuntu
---

### Post by Dominik_Hartwich on 2017-04-28
hello,
after clean installation of ubuntu 16.04 i cannot connect with me ebook in read/write mode.
after "mount" I have what below:

```

....
/dev/sdb on /media/domi/Story HD type vfat (rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2


```

could you give me a solution?

---

### Post by cariboo on 2017-04-28
I may be misunderstanding your problem, but I use an inexpensive RCA tablet for an ebook reader, it connects automagically when I plug in the usb cable:

```
usb 2-4: new high-speed USB device number 3 using ehci-pci
[27186.294553] usb 2-4: New USB device found, idVendor=1914, idProduct=201d
[27186.294557] usb 2-4: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[27186.294560] usb 2-4: Product: MT65xx Android Phone
[27186.294562] usb 2-4: Manufacturer: MediaTek
[27186.294564] usb 2-4: SerialNumber: 85CUSKAABY7TAYZD
```

---

### Post by leunam12 on 2017-04-29
Maybe if you give more details somebody will be able to help you. What I understand from your post is that you have and ebook reader and you plug it in to your computer via USB and it mounts but you are not able copy files to it. If so, what is the brand name and model? Is it and android device?

---

### Post by Dominik_Hartwich on 2017-05-11
Hello again,
after short holiday, i did the simpliest thing - clean install of calibre.
Now everything works fine.
Thanks for help.

dOMI

---

