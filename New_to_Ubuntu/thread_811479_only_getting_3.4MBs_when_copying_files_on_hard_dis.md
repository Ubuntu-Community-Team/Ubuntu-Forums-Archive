---
title: "only getting 3.4MB/s when copying files on hard disk"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by breadbin on 2008-05-29
Hiya, I am running hardy heron 8.04 64-bit and copied a 800Mb file from one folder to another on the same partition. EXT3 is the filesystem. it took 4 minutes. do i need to get special drivers for the hard disk or mobo? 

my computer is

Athlon 3800+
1 Gig Ram
Asus M2ne mobo
Seagate 250gb - can't remember the model but its way faster than that normally.

any help would be appreciated. thanks

---

### Post by kpkeerthi on 2008-05-29
Check if DMA is enabled
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

---

### Post by breadbin on 2008-05-30
Tried sudo hdparm /dev/sda3 (which is the /home folder)

/dev/sda3:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 30401/255/63, sectors = 195318270, start = 42973875

doesn't mention anythign about DMA like the link suggests, any clues?

---

### Post by breadbin on 2008-06-04
I didn't get this sorted but it doesn't seem to make a difference really in real life. Its not that often i'd be copying big files. It depends on the size of the files too because with 5 megapixel photos it shoots up to 25-30 mb/s. Maybe that might jog someones memory. the hdparm test shows nearly 60mb/s so i don't know what to think now.

---

