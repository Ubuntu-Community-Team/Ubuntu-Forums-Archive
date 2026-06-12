---
title: "Questions about mounting and gnome-volume-manager"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2008-07-12
Hi, I have a few questions about-mounting drives and mount points.

-How do I manually mount a partition with the terminal?

-If I am correct, gnome-volume-manager is responsible for automatically mounting usb drives when they are connected.  How do I change the mount point that GVM automatically mounts the drive to?

Thanks!

:)

---

### Post by iaculallad on 2008-07-12
To manually mount a partition/device using the terminal:

```
sudo mount -t vfat /dev/hda2 /mnt/winc
```

Your **/dev/hda2** is source and **/mnt/winc** is target, mounting it w/ FAT32 filesystem.

Yes you are correct, GVM is responsible for the automatic mounting of storage devices. If an authenticated user is logged in, in the graphical desktop environment (either KDE or GNOME), user should have the GNOME Volume Manager running in background.  GNOME Volume Manager listens to the system bus events and is notified when hald send "hardware added/removed" events. You can't change the mount point volumes in-the-fly since GVM uses the mtab w/c is automatically edited when mount command is invoked or new storage devices are inserted.

---

### Post by pi.boy.travis on 2008-07-12
OK, so if I need a usb drive mounted in a place other than /media/XXX , I can unmount it and then manually mount it to a new mount point.  How would I go about doing that?

Thanks!

---

