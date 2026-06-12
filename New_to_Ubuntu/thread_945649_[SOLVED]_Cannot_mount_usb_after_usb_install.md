---
title: "[SOLVED] Cannot mount usb after usb install"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by duruttye on 2008-10-12
Hello!

I've been having this annoying problem since I installed ubuntu 7.10 from an usb stick.
This is what I used to make the usb bootable and to make it install the OS.
[http://startx.ro/sugar/isotostick.sh](http://startx.ro/sugar/isotostick.sh)
After that, this is what I get in dmesg (guessing it searches for a cd-rom...)
[HTML]dmesg | tail
[ 4052.145903] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 4052.147501] sd 7:0:0:0: [sdb] 2015231 512-byte hardware sectors (1032 MB)
[ 4052.147998] sd 7:0:0:0: [sdb] Write Protect is off
[ 4052.148015] sd 7:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 4052.148021] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 4052.148031]  sdb: sdb1
[ 4052.261279] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[ 4052.261575] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 4053.031134] UDF-fs: No VRS found
[ 4053.076256] ISOFS: Unable to identify CD-ROM format.
[/HTML]

After I installed ubuntu 7.10 from this usb stick, NO usb sticks worked whatsoever, it was the same error message.

Strangely, in Gparted, it has the mount point /media/cdrom and after a few tries I can mount it in that folder...
The next problem is, that I'm using 8.10, because 8.04 did't work out for me at all, but I don't think that that's the problem, because, this happened exactly in the same way in Ubuntu 7.10.

So, if any of you have any ideas, I will gladly follow instructions.
Have same basic knowledge in using the terminal.

Thank you all!

---

### Post by nothingspecial on 2008-10-12
If you don`t have a dvd/cd drive try -



```
gksudo gedit /etc/fstab
```

Then look for a line similar to

```
/dev/sdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

Comment it

```
#/dev/sdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

Save and reboot.

If that doesn`t work then uncomment it (remove the #) save and reboot again.

Don`t try this if you do have a dvd/cd drive.

---

### Post by duruttye on 2008-10-12
Well, fortunately I do have a cd/dvd drive.
Any other ideas?

I installed from USB, because it is a lot faster and I didn't have a cd to write to...

---

### Post by nothingspecial on 2008-10-12
> **duruttye said:**
> 

I installed from USB, because it is a lot faster and I didn't have a cd to write to...

I find it faster too. Don`t know what`s up though, sorry.

---

### Post by duruttye on 2008-10-13
WOW
yesterday I tried twice what you suggested, it didn't work, but today it did!

I don't know what is the difference, and I don't even care!!

Thanx!!!

---

### Post by nothingspecial on 2008-10-13
Cool

:guitar:

---

