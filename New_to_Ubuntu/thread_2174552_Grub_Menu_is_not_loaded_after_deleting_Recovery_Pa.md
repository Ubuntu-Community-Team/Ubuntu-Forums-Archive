---
title: "Grub Menu is not loaded after deleting Recovery Parition- Acer D257 Netbook"
date: 2013-09-15
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2013-09-15
I have an Acer aspire D257 netbook with dual boot- Ubuntu 12.04 and Windows 7 starter. Few hours back I was reading an article about deleting the recovery partition used by windows 7. I logged into windows 7 and formatted the 13Gb recovery partition using the software "EaseUS". New partition was created and it worked fine. When I restarted the netbook,  acer start up screen is showed and the screen goes black after a while. The grub menu is not show. Did the windows 7 messed up the grub ? How to bring back the grub bootloader back? 

[http://www.howtogeek.com/139710/remove-your-pc%E2%80%99s-recovery-partition-and-take-control-of-your-hdd/](http://www.howtogeek.com/139710/remove-your-pc%E2%80%99s-recovery-partition-and-take-control-of-your-hdd/)

---

### Post by grentthevampire on 2013-09-15
You can fire up a LiveOS on your USB then run a boot-repair
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by 1991sudarshan on 2013-09-15
> **grentthevampire said:**
> You can fire up a LiveOS on your USB then run a boot-repair
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thank you for the link. But I fixed the issue by going through this one. 
[http://opensource-sidh.blogspot.in/2011/06/recover-grub-live-ubuntu-cd-pendrive.html](http://opensource-sidh.blogspot.in/2011/06/recover-grub-live-ubuntu-cd-pendrive.html)
The windows 7 messed up with MBR and grub I guess.

---

