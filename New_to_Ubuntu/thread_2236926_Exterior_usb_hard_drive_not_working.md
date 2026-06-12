---
title: "Exterior usb hard drive not working"
date: 2014-07-29
forum: New to Ubuntu
---

### Post by openation1 on 2014-07-29
Hello... I have Ubuntu 14.04 on my external usb hard drive and I was using it on my desktop computer....... I tried to put it on my laptop and now it doesn't work please help me thank you

---

### Post by Vladlenin5000 on 2014-07-29
It won't work unless the GRUB is installed there and most certainly it was/is installed in the desktop's internal drive.

---

### Post by oldfred on 2014-07-29
Go back to Desktop and boot external drive.
Is system UEFI or BIOS?

If BIOS, you can just install grub to sdb (if external is sdb, not some other)

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

If UEFI post this:
sudo parted -l

---

