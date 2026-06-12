---
title: "How to sync folders when any USB drive is mounted"
date: 2010-08-02
forum: Programming Talk
---

### Post by OlyPerson on 2010-08-02
Hey,

I need to create a system that syncs a folder on my laptop with any USB drive that is connected but I'm having a couple issues.

First, I can write udev rules for a script to run when a specific USB device is mounted, but not for any generic USB flash drive.  My current udev rule I've created is:
```
ATTRS{serial}=="0d0g9d890", SYMLINK="usb_drive", RUN+="/usr/bin/my_script"
```

Second, the script I've written doesn't work when ran by the udev rule thing, but works when I run it in the terminal.  I think this has to do with permissions of the USB drive, but I don't know how to work with FAT16/32 permissions.  Here is my code:
```
#! /bin/bash
# This is a simple script that syncs folders

rsync -vaz /home/me/Documents/sample /media/UDISK/sample
```
I also need to learn a way to make it so any usb drive in /media is used instead of me having to specify which drive I want specifically.

Thank you guys for any help, it's really appreciated!:D

---

### Post by Jacobian on 2010-08-03
Would something like this help?
[http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/](http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/)

---

### Post by OlyPerson on 2010-08-03
> **Jacobian said:**
> Would something like this help?
[http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/](http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/)

Thanks for the reply, I've already read that though (was my main source of info, so good find).

I worked on this a while longer yesterday and it seems my only issue now is permissions on the USB drive.  When I plug in the drive I can write a script that writes to a file on my computer but not on the USB device.  I've tried writing an fstab entry here to give me full permissions on it:
```
/dev/sdb1     /media/usb_drive   vfat    users,umask=000   0  0
```
This mounts the device in /media and it shows that it has full permissions but it doesn't work still.


For reference, in case anyone is reading this to get the same question answered, you can write a udev rule that identifies any USB device just by having this in your rule:
```
SUBSTEMS=="usb"
```
and no ATTRS specifications.  Works for me.

---

