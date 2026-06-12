---
title: "[SOLVED] External Hardrive not working"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by mojo123 on 2008-08-30
When ever i go to my external hard drive (WD Passport), i get a message saying "You are not privileged to mount the volume "WD Passport". I tried entering it through "gksudo nautilus", but i get another error saying "Unable to mount the volume "WD Passport fuse:failed to access mountpoint /media/ hd-nfts:No such file or directory.

My hd is formated as NFTS.

---

### Post by swoll1980 on 2008-08-30
did you try to set up your authorizations? I'm just grapping at straws here no real knowledge on the subject

---

### Post by knattlhuber on 2008-08-30
> **mojo123 said:**
> When ever i go to my external hard drive (WD Passport), i get a message saying "You are not privileged to mount the volume "WD Passport". I tried entering it through "gksudo nautilus", but i get another error saying "Unable to mount the volume "WD Passport fuse:failed to access mountpoint /media/ hd-nfts:No such file or directory.

My hd is formated as NFTS.

Does the folder /media/hd-nfts exist? If not, you need to create it and set the permissions so that you have full r/w access to it. Did you spell the mountpoint correctly when you tried to mount it? The file system is actually abbreviated NTFS (you swapped T and F).

---

### Post by mojo123 on 2008-08-30
I just made the folder /media/hd-nfts, and put full rights on it, but i still get the same error.

---

### Post by gmxgeek on 2008-08-30
Can you type out the full command you are using to mount? Or are you using gui?

---

### Post by mojo123 on 2008-08-30
Im using the GUI

---

### Post by gmxgeek on 2008-08-30
I don't suppose you know the HD address of the external drive? hdx,x?
I'm kinda taking shots in the dark here as well.

---

### Post by mojo123 on 2008-08-30
I think its hd1,0

---

### Post by gmxgeek on 2008-08-30
try
```

sudo fdisk -l

```
and see if it shows up there.
if so, then try
```

sudo mount -t ntfs /dev/hdaX /mount/hd-ntfs

```
where x is the number found in fdisk

---

### Post by knattlhuber on 2008-08-30
How about this:

```
sudo apt-get update
sudo apt-get install ntfs-config
```

and then run the program from Applications/System Tools and pick the drive. Restart the computer. The drive should be mounted automatically then.

---

### Post by mojo123 on 2008-08-30
> **knattlhuber said:**
> How about this:

```
sudo apt-get update
sudo apt-get install ntfs-config
```

and then run the program from Applications/System Tools and pick the drive. Restart the computer. The drive should be mounted automatically then.

I've done this same error


```
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS
```

This is my sudo fdisk -l

---

### Post by gmxgeek on 2008-08-30
Have you tried manually mounting the drive from terminal?

---

### Post by knattlhuber on 2008-08-30
Please post the output of
```
cat /etc/fstab
```

---

### Post by mojo123 on 2008-08-30
I've fixed it! Thanks guys

---

### Post by knattlhuber on 2008-08-30
> **mojo123 said:**
> I've fixed it! Thanks guys

Cool. Glad it works now. Can you please post what exactly you did to make it work (for the next person with the same problem)?

---

