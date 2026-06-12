---
title: "Copy failure with external USB on Live Ubuntu"
date: 2019-06-24
forum: New to Ubuntu
---

### Post by mlippitt on 2019-06-24
I'm trying to recover Windows 10 folders on a PC with Live Ubuntu 18.04.2 LTS.
Windows is toast. The intention is to copy user folders to a destination drive.
I plug in an external USB drive for the destination and it appears in the Ubuntu file manager
and Disks dialog like this:
/dev/sdb1   mounted at media/Ubuntu/MyPassport
It's an NTFS partition and the User Session Defaults are ON

I drag and drop a folder from the source to the destination and the copy starts.
The process indicates 100 or so successful file copies and then consistently gets an
input/output error on the destination device, typically a file or directory create error
but it varies.
When the error occurs the destination device is no longer on the file manager screen or
the Disks dialog, as if the device has been unmounted. I’m wondering if this unmounting caused the input/output errors? And how to keep this unmounting from happening?

I can unplug and plug the external USB drive and it reappears.
Any help would be much appreciated.

---

### Post by oldrocker99 on 2019-06-24
NTFS is still not very reliable. Install the Gnome Disk Utility:
```
sudo apt install gnome-disk-utility
```

First, look at the disk, click on the gears icon, and select "Check Filesystem."

If there is a problem found, plug the drive in and format it as Ext4. It is an advanced file system, which is a lot better than NTFS.

Good luck. There is a program called anyfs-tools available on SourceForge which does not destroy data, but it requires compiling, and, while easy once you've done it, it's not for a new user to attempt.:(

It is quite possible that you'll have no problems using ext4. Good luck!

---

### Post by mlippitt on 2019-06-24
Thanks oldrocker99, I'll give this a try.

---

### Post by mlippitt on 2019-06-25
I really thought this was going to work and then it didn't.

Formatted the destination USB drive to ext4, started up the copy, saw the progress display get over 1300 files, and then the error messages started and the drive had disappeared from the file manager and Disks utility.

I tried to retry but now the drive shows in file manager and Disks utility for about 2 seconds and then disappears. This is very repeatable. I get the same result with the sudo fdisk -l command line. The drive is listed one second and gone the next.

Could there be some security function that is kicking the drive out of the system? I'm runnnig [COLOR=#000000]Live Ubuntu 18.04.2 LTS
[/COLOR]

---

### Post by rbmorse on 2019-06-25
Could be a cable or power issue with the USB drive. Try a different cable, preferably a short one, and connect the drive to an external power source if possible.

---

### Post by mlippitt on 2019-06-25
Thanks rbmorse,
Since the cable and disk wrote 300+GB on a windows desktop last night without a hiccup the hardware is looking good.
But that idea made me wonder if there is some power management firmware/hardware interaction going on between the HP-S5000, the WD Passport, and Ubuntu. So I bought a 256GB flash drive, formatted to EXT4 and it ran a four hour copy job to completion without error. Thats progress. Next I'm going to try to do this with the flash formatted to NTFS since I'm not having any success getting Ext2Fsd working, windows sees ext4 and all it wants to do is format.

---

