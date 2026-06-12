---
title: "Ubuntu Booting Problem"
date: 2013-09-03
forum: New to Ubuntu
---

### Post by cm-humayun on 2013-09-03
I had Ubuntu 12.04 LTS installed on my laptop occupying 45 GB of space.

Due to some reason i have to re-Install windows 7-32 bit and because of this i lost my booting option which directs me to chose Ubuntu or windows.Although i haven't restored my occupied space.

I want to know whether my Ubuntu has left
if(yes) then what should i restore to restore my boot.and 
if(no) what should i do to restore my occupied space.because disk space is not appearing in the My comupter of OS Windows 7

---

### Post by VMC on 2013-09-03
Everyone these days are using [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). But first, using the livcd, open a terminal and type the output of this, so we can know for sure if you still have Linux partitions.

```
sudo fdisk -l
``` [lower case L]

edit: once booted to desktop, type *Ctrl+Alt+t* should get you a Terminal.

---

### Post by cm-humayun on 2013-09-03
After i have opened the iso file in a virtual CD-Rom.I find this [IMG]https://skydrive.live.com/#cid=03ED65E15756DEDF&id=3ED65E15756DEDF%21107&v=3[/IMG]
[https://skydrive.live.com/#cid=03ED65E15756DEDF&id=3ED65E15756DEDF%21107&v=3](https://skydrive.live.com/#cid=03ED65E15756DEDF&id=3ED65E15756DEDF%21107&v=3)

---

### Post by kingsuk-d on 2013-09-03
The problem is that your  Windows is not able to detect the Ubuntu  partition (Windows is not capable of doing that ) and when you installed Windows it has overwriiten the Ubuntu bootloader (grub) in MBR with its own.  You need to reconfigure the grub . You can do it using a LiveCD and mentioned in the prev reply.

---

### Post by kingsuk-d on 2013-09-03
You need to load Ubuntu iso into a USB  and make it bootable (If you do not have a Ubuntu DVD/CD) and then boot from USB i think.

---

### Post by cm-humayun on 2013-09-03
Ok. I try

---

