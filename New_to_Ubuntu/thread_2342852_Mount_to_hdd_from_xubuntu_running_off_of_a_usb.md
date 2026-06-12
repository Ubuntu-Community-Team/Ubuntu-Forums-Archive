---
title: "Mount to hdd from xubuntu running off of a usb"
date: 2016-11-10
forum: New to Ubuntu
---

### Post by mexikyan on 2016-11-10
So im new to all of this and im running xubuntu off of a usb. whenever i click 999GB volume in the file manager i get this message

Error mounting /dev/sda2 at /media/xubuntu/4202A94D02A946AF: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999" "/dev/sda2" "/media/xubuntu/4202A94D02A946AF"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

i just want to be able to acess the stuff from my hard drive. I use windows 10 when im not using linux.

---

### Post by yancek on 2016-11-10
The message you posted means that you left your windows system hibernated (which is the default) and no Linux system will mount it for access as it makes corruption probable.  So don't do the standard shutdown but do a complete shutdown turning off fastboot and hibernation.

---

### Post by mexikyan on 2016-11-11
do I do that in the bios?

---

### Post by oldos2er on 2016-11-11
You need to boot into Windows to turn off hibernation and fast restart.

---

### Post by mexikyan on 2016-11-11
> **oldos2er said:**
> You need to boot into Windows to turn off hibernation and fast restart.

Thank you!

---

