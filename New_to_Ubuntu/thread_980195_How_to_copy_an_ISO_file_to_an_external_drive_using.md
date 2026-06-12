---
title: "How to copy an ISO file to an external drive using the command line"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by jlbr21 on 2008-11-12
Hi,

I am a bit confused about using the cp command. I got an .iso file and its pretty large, 8.1 Gb and want to copy it to an external drive, I tried to do it manually, as in right clicking the file, selecting copy and then go to the external drive and right click and paste, and halfway through I get an error message saying there was a mistake since the file is too big. I figured if i did it from the command line it would be foolproof but I cant seem to get it right, I tried this:

juanluis@juanluis-laptop:/tmp$ cp HP_RECOVERY.iso ~ /media/DRIVE 2
cp: target `2' is not a directory

DRIVE 2 is the name I gave to my external disk. When I right click on it and go to Properties, thats the mount point I get, thats why I type it like that.

What am I doing wrong?

---

### Post by eriqjaffe on 2008-11-12
Try it like this:

```
cp HP_RECOVERY.iso "~/media/DRIVE 2/"
```

---

### Post by unutbu on 2008-11-12
Try
```

cp HP_RECOVERY.iso "/media/DRIVE 2"
```
I removed the tilde (~) because I assume the drive is mounted at /media, not ~/media. Is that correct? Either way, you need the quotation marks to "protect" the space in the name "DRIVE 2".

Also, what type of filesystem is "/media/DRIVE 2"?
(e.g. vfat, fat32, ntfs, ext3, etc.)

Each filesystem type has a different maximum file size limitation. For example, fat32 has a maximum file size of 4 GB minus 1 byte. (See [http://en.wikipedia.org/wiki/Fat32](http://en.wikipedia.org/wiki/Fat32)).
Thus your 8.1GB file can not be copied onto a fat32 filesystem as a single file.

If you search wikipedia for other filesystem types, you will find there the maximum file size each supports.

---

### Post by jlbr21 on 2008-11-12
Its a FAT filesystem, im trying it out the way you mentioned, with the tilde it did not work as you said, seems to be working.


Thanks!

---

### Post by jlbr21 on 2008-11-12
Ah, ok, didnt read the second part of your message, OK, it wont work then, since its a FAT.

---

### Post by jlbr21 on 2008-11-12
Nope, did not work, do you have any suggestions? I would appreciate it. Thanks.

---

### Post by handydan918 on 2008-11-12
> **jlbr21 said:**
> Nope, did not work, do you have any suggestions? I would appreciate it. Thanks.

Use a real fie system?

---

### Post by jlbr21 on 2008-11-12
OK... nevermind.

---

### Post by eriqjaffe on 2008-11-13
If you have access to a Windows PC, you can convert the drive's filesystem from FAT32 to NTFS.

```
convert drive_letter: /fs:ntfs 
```

---

### Post by jlbr21 on 2008-11-13
The drive is formatted to VFAT because I think its the best way to share files between Linux, Mac and Windows. So I did consider re-formatting, but I dont know if its such a good idea. Thanks anyway.

---

### Post by snova on 2008-11-13
Stick with VFAT. You'll be fine.

If you're getting an error, post it.

---

