---
title: "installing ubuntu with separate partition for home"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by bovus on 2008-05-03
Hi, I want to make a fresh installment of 8.04 with a separate partition for home directory.  Can anyone give me step by step instructions or point me to a good tutorial?  Thanks

---

### Post by aheckler on 2008-05-03
Do a regular install, but when you get to the partitioning part, choose manual.

Make your partitions like this:

/ = 10 GB with ext3 (beginning of the drive)

then

swap = 1-2 GB (end of the drive)

finally

/home = the rest of the disk with ext3


EDIT: That looks way more complicated than it it, let me find a good guide here...

---

### Post by aktiwers on 2008-05-03
> **bovus said:**
> Hi, I want to make a fresh installment of 8.04 with a separate partition for home directory.  Can anyone give me step by step instructions or point me to a good tutorial?  Thanks

When you get to the partitioning part of the install choose "manual".

Create a partition for SWAP drive (about 1gb) pick SWAP as format.
Create a partition for your system (min 4.gb) in EXT3 format and with mountpoint /
Create your Home partition in EXT3 format with mountpoint /home

Remember Linux is CaSeSeNsItIve so /home is with small letters.

Hope this helps :)

---

