---
title: "Formats for removable storage"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by Dom Rivers on 2008-08-12
Hi,
  I've got a couple of USB drive caddies, one SATA with a 250GB WD hard drive in it, partitioned into two in NTFS to use as a back up for my wifes laptop and one IDE caddy with no hard drive at present.
  I don't seem to be able to access the NTFS one to view the Jpegs so I'm going to use the IDE caddy as my own dedicated back up storage (see other thread](*,), given that I'm going to fit a blank unformatted 500GB IDE drive in it how do I get it viewed as extra storage by Ubuntu, will it just plug and play (like a USB stick) or am I going to have to enter some more magic spells :) in terminal.

---

### Post by LowSky on 2008-08-12
Ubuntu can read NTFS, but you need to add the support go to Add/Remove, look for NTFS-config (typing just NTFS should get it to pop up), once installed run it and turn o read/write support and auto mount.

Otherwise I suggest using FAT32 for formating the newer drive. This way it will be natively supported by linux and windows, **but **files cannot be larger than 4GB

---

### Post by Dom Rivers on 2008-08-12
I already had it installed it seems to only give me the options to enable write support for internal device and/or enable write support for external device,nothing about auto mount.

---

### Post by Dom Rivers on 2008-08-12
I'm still "not priveliged" to open one partition and unable to mount the other

---

### Post by WRDN on 2008-08-12
Plug the drive in, and then open the Terminal, and type:

```
sudo fdisk -l
```

This will allow you to identify the device- it will be /dev/sda[n] or /dev/hda[n] (where [n] is  number).

Now, type:

```
sudo chown [username] /dev/[device]
```

Replace [username] with your username, and [device] with the device the partition corresponds to.

This will change the permissions to allow you to access the drive.

---

### Post by bodhi.zazen on 2008-08-12
For some reason, Ubuntu like FAT. Other files systems, on removable devices such as NTFS and ext3 seem to be problematic. I do not know why (has not bothered me enough to figure out ... I like incantations)

---

