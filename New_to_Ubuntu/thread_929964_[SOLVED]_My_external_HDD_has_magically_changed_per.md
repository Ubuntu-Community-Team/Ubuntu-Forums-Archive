---
title: "[SOLVED] My external HDD has magically changed permission"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by billgoldberg on 2008-09-25
I suddenly have read-only access to my external HDD.

I tried going to the drive in a nautilus as root and change permissions, it didn't work.

I need to know two things:

1. how did this happen?

2. how to I retain full read-write access again?

[I]ps: this drive is used on my ps3, laptop and desktop.

The only other person using it is my brother. He couldn't change permissions if his life depended on it.[/I]

Oh, and one of the folders is filled with loads of files with gibberish file names. Properties tells me they are of the "application/octet-stream" type.

---

### Post by LowSky on 2008-09-25
is it ntfs formated?
if yes this sometimes happens when the  drives is disconnected imporperly during removale or shut down. Booting into Windows and doing a proper shutdown usually will fix the issue

---

### Post by sisco311 on 2008-09-25
plug in the disk and post:
```
dmesg | tail -n 20
```

---

### Post by billgoldberg on 2008-09-25
This is the ls -l command

-rwx------  1 rw root 77544 2008-08-31 18:52 99982022_17622d885a.jpg
drwx------ 13 rw root 32768 2008-08-31 18:53 Music
drwx------ 18 rw root 32768 2008-08-31 18:58 Pictures
-rwx------  1 rw root  5120 2008-09-11 18:53 Thumbs.db
drwx------  7 rw root 16384 2008-09-25 20:36 Videos


from what I read from that, I own the drive.

So I don't get why I can't change permissions.

---

### Post by billgoldberg on 2008-09-25
> **sisco311 said:**
> plug in the disk and post:
```
dmesg | tail -n 20
```

[ 4651.492371] usbcore: registered new interface driver usb-storage
[ 4651.492382] USB Mass Storage support registered.
[ 4651.492966] usb-storage: device found at 3
[ 4651.492972] usb-storage: waiting for device to settle before scanning
[ 4654.129127] usb-storage: device scan complete
[ 4654.129885] scsi 2:0:0:0: Direct-Access     WD       5000AAK External 1.06 PQ: 0 ANSI: 0
[ 4654.141593] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[ 4654.142244] sd 2:0:0:0: [sdb] Write Protect is off
[ 4654.142249] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 4654.142252] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 4654.143304] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[ 4654.143834] sd 2:0:0:0: [sdb] Write Protect is off
[ 4654.143838] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 4654.143841] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 4654.143852]  sdb: sdb1 sdb2 < sdb5 >
[ 4654.171106] sd 2:0:0:0: [sdb] Attached SCSI disk
[ 4654.171186] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 4743.951444] FAT: Filesystem panic (dev sdb1)
[ 4743.951459]     invalid access to FAT (entry 0xc20e004a)
[ 4743.951463]     File system has been set read-only

--

The last three lines tell me what's wrong.

How do I fix it?

---

### Post by Crafty Kisses on 2008-09-25
This has happened to me in the past, what I did to solve the issue was unmount the drive, and the command should be something similar to this:
```
sudo umount /dev/sdb1 
```
Then I checked the HDD:
```
sudo fsck /dev/sdb1
```
Then it seemed to work, try that and see if that springs your HDD to life.

---

### Post by billgoldberg on 2008-09-25
> **Codename said:**
> This has happened to me in the past, what I did to solve the issue was unmount the drive, and the command should be something similar to this:
```
sudo umount /dev/sdb1 
```
Then I checked the HDD:
```
sudo fsck /dev/sdb1
```
Then it seemed to work, try that and see if that springs your HDD to life.

Nope didn't work.

---

### Post by billgoldberg on 2008-09-25
Switching computers didn't work either. It was a long shot anyhow.

I really need write access to this drive asap.

Dammit.

These things also happen when you need to get stuff done.

---

### Post by Crafty Kisses on 2008-09-25
Can you read the files from the drive? Look if the following command gives you any errors
```
dmesg
```

---

### Post by prshah on 2008-09-25
> **billgoldberg said:**
> 
[ 4743.951444] FAT: Filesystem panic (dev sdb1)
[ 4743.951459]     invalid access to FAT (entry 0xc20e004a)
[ 4743.951463]     File system has been set read-only
How do I fix it?

> **Codename said:**
> 
```
sudo fsck /dev/sdb1
```


That last command (after unmounting) should read ```
sudo fsck -a /dev/sdb1
``` for check / auto-repair. Note you _can_ potentially lose files on the autocheck. (legal speak nonsense, in real world terms you probably have no other choice.)

---

### Post by billgoldberg on 2008-09-25
> **prshah said:**
> That last command (after unmounting) should read ```
sudo fsck -a /dev/sdb1
``` for check / auto-repair. Note you _can_ potentially lose files on the autocheck. (legal speak nonsense, in real world terms you probably have no other choice.)

I'm trying it now.

---

### Post by billgoldberg on 2008-09-25
Adding the "-a" to the command did the trick.

Thanks.

---

