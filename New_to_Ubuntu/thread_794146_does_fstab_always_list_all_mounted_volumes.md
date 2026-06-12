---
title: "does fstab always list all mounted volumes?"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by loldrup on 2008-05-14
In that case, it fails to list my otherwise perfectly mounted USB stick.

I'm trying to figure out which /dev/ device my USB stick really is, so that I can format it with a real filesystem (ext3 rather than the current vfat..)

I'm using ubuntu 7.10

---

### Post by rockerphil on 2008-05-14
what's the output of this code?

sudo fdisk -l

---

### Post by TeoBigusGeekus on 2008-05-14
Fstab lists only the drives that are mounted on bootup. 
To format your flash stick, open gparted - if you don't have it:
```
sudo apt-get install gparted
```

from system->administration->partition editor, let it see all your drives and then do your stuff...

---

### Post by jimv on 2008-05-14
Fstab lists all the volumes that Ubuntu found and mounted during install, as well as anything that you manually added to the file.

---

### Post by nick_h on 2008-05-14
No. The file that lists mounted devices is /etc/mtab.  You can also see mounted devices by typing:
```
mount
```

---

### Post by tgm4883 on 2008-05-14
> **loldrup said:**
> In that case, it fails to list my otherwise perfectly mounted USB stick.

I'm trying to figure out which /dev/ device my USB stick really is, so that I can format it with a real filesystem (ext3 rather than the current vfat..)

I'm using ubuntu 7.10

No, fstab lists what auto mounts at boot.

---

### Post by bodhi.zazen on 2008-05-14
no, not at all

removable devices are managed by gnome-volume-management and udev

To list your devices :

```
sudo fdisk -l
```

The "problem" is the device may change designation, /dev/sda1 to /dev/sdb1 , etc.

To solve this, make a label

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 
Or mount the device with UUID

---

### Post by dizee on 2008-05-14
USB flash drives are usually something like /dev/sdb1.

---

### Post by rockerphil on 2008-05-14
i personally have 2 internal hard drives, so a USB drive shows up as /dev/sdc

---

### Post by loldrup on 2008-05-14
> **rockerphil said:**
> what's the output of this code?

sudo fdisk -l

That solved my problem. It turns out it had the name /dev/sdb1

Thank you :)

---

### Post by BlueSkyNIS on 2008-05-14
> removable devices are managed by gnome-volume-management and udev

Is HAL has anything to do with it?

---

### Post by az on 2008-05-14
> **BlueSkyNIS said:**
> Is HAL has anything to do with it?

HAL is in between gnome-volume-manager and udev.

The quickest way to see your devices is to run

cat /proc/partitions

You can also see your drives by running

sudo lshw -C short -disk

but that will not display individual partitions.

Another way to do it if, for example, you use several usb drives at the same time, you can run
tail -f /var/log/messages
and then plug in your device.  Look at the messages appear as your device is detected.  Instead of running that, you can use the log tool and peek at the "messages" log.

---

