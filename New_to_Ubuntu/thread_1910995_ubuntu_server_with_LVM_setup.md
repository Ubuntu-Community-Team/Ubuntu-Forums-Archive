---
title: "ubuntu server with LVM setup"
date: 2012-01-18
forum: New to Ubuntu
---

### Post by just_cruising on 2012-01-18
Noob to linux servers here, I'm after a bit of advice on the best way to do what i want. i have the following hard drive setup

1x320gb OS-Ubuntu Server
1x1tb home photos/videos
1x1tb home photos/videos

Aim is to setup the 2x1tb drives in RAID1, I want to do this via LVM. How can I achieve this, as when I installed ubuntu server I didn't select LVM.

From what I have read LVM needs to be on the OS drive before you can create the RAID1 setup?

---

### Post by gsgleason on 2012-01-18
What I have done is set up the two drives as linux raid autodetect via fdisk, then add those to one raid array, then create the lvm on that raid array.

---

### Post by just_cruising on 2012-01-19
> **gsgleason said:**
> What I have done is set up the two drives as linux raid autodetect via fdisk, then add those to one raid array, then create the lvm on that raid array.

So I assume that you have done this after installing Ubuntu server or was it during the partitioning in the OS setup?

---

### Post by gsgleason on 2012-01-19
After installation.  These were separate drives from the rest of the os.

---

### Post by just_cruising on 2012-01-20
> **gsgleason said:**
> After installation.  These were separate drives from the rest of the os.

Yeah, thanks I just did a fresh rebuild last night now to get a gui going till I get my head around the command line. Then to install webmin as well.

---

### Post by just_cruising on 2012-01-20
thinking im going to scrap the server idea and run the desktop version. It will work better for me as I have the GUI and can also watch content as well.

---

