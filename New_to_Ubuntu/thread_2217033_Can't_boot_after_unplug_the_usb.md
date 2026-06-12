---
title: "Can't boot after unplug the usb"
date: 2014-04-15
forum: New to Ubuntu
---

### Post by ram13 on 2014-04-15
I have ubuntu server 13.10 installed on a usb flash drive (partition: /boot, /boot/efi, / (LVM), swap(LVM)), it works very fine, I can reboot, shutdown and restart.

Recenly I unplugged the ubuntu installed usb flash drive and plugged a windows (HDD) for some reason. Afterwards I put back ubuntu usb flash drive (unplugged windows), now ubuntu no longer boots. I had the same issue before and I reinstalled the whole ubuntu.

How can I fix this issue now? thanks

---

### Post by buzzingrobot on 2014-04-15
If you didn't unmount the USB or shutdown the machine before removing it, it is possible it was damaged.

---

### Post by sudodus on 2014-04-15
> **buzzingrobot said:**
> If you didn't unmount the USB or shutdown the machine before removing it, it is possible it was damaged.
+1

It takes longer for the cached data to be written to a USB drive compared to an internal drive, particularly if it is a USB 2 drive or USB 2 system in the computer, and particularly it is a standard USB pendrive with slow flash memory. Use what signs that you can find (LED indicators etc) to be sure the computer is really switched off before unplugging.

Edit: see also this link

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

### Post by ram13 on 2014-04-15
How do I fix it now? I spent lot of time to configure. Thanks

---

### Post by sudodus on 2014-04-15
0. To prevent future problems, take backups :-)

1. Maybe it works to try to repair the file system, when booted from another linux system.

Boot from another linux system, for example an Ubuntu install drive.

Identify the root partition of this USB drive, that is borked.

Run this command from a terminal window (or text screen)

```
sudo e2fsck -f /dev/sdxy
```

where x is the drive letter and y is the partition number, for example /dev/sdb1 but check what it is in your case, for example with

```
sudo parted -l
```
and 
```
df
```

---

