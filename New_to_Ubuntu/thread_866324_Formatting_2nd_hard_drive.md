---
title: "Formatting 2nd hard drive"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by rsnow on 2008-07-21
I have installed a 2nd hard drive and it is showing as DRV_VOL1. Shouldn't I format it so that its size will be reflected in its properties? How do you format or otherwise configure a 2nd hard drive. I do not have plans to use it immediately but would like to have it ready.

---

### Post by ibutho on 2008-07-21
You can use gparted to create partitions on the disk (you probably need to format them as ext3 or reiserfs) and the create entries for the partitions in /etc/fstab.

---

### Post by ibuclaw on 2008-07-21
DRV_VOL1 is the name that is being shown on the Gnome Desktop, I presume?

You can change the name of it rather simply without re-formatting.

What is the output of this command in the terminal?
```
df -T --exclude tmpfs --exclude fuse.gvfs-fuse-daemon
```
Regards
Iain

---

### Post by rsnow on 2008-07-21
the output of the command is

Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda1     ext3   113892200   3180712 104926084   3% /

---

### Post by ibuclaw on 2008-07-21
Oh, your second drive isn't mounted then...
OK, what is your second hard-drive's filesystem type?

Regards
Iain

---

### Post by rsnow on 2008-07-21
"OK, what is your second hard-drive's filesystem type?"

Not sure what to reply. The drive is fresh out of the box, jumpered as slave and connected up and machine booted.

---

### Post by logos34 on 2008-07-21
To change the name:

sudo tune2fs -L newlabel /dev/sda?

Create permanent mount and add it to /etc/fstab so it automounts at boot.

sudo mkdir /media/sda?

gksudo gedit /etc/fstab

> # /dev/sda?  
UUID=xxx-xxx-xxx /media/sda? ext3 defaults 0 2find UUID with:

sudo blkid

---

### Post by ibuclaw on 2008-07-21
Sorry. Presuming that it is connected, run
```
sudo fdisk -l
```

That will show you what drive it is :)

Regards
Iain

---

### Post by rsnow on 2008-07-21
The sudo blkid and sudo fdisk -l did not get any results. Here is what came up after gedit etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=3304e03b-eec5-4bec-95f6-f67c0c37046e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=67a48a6c-e35c-4498-9e29-f5d985906112 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by ibuclaw on 2008-07-21
fdisk -l doesn't work?

That doesn't make sense... how do you mean "doesn't work"?

There is a howto on Renaming Drives here:
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Simply follow that, and instead of putting in a label for your second hard-drive, just leave it blank, and on reboot Gnome will register it as its drive size.

Regards
Iain

---

### Post by rsnow on 2008-07-21
The first time I typed sudo fdisk -l nothing happened. Now when I type it I get the info about both drives. I'm not sure what happened the first time. Thanks for the help and the link. I'm sure I'll be back with other issues but I'll try not be a pain. I need to train myself to do more reading before bugging others. Hopefully, someday, I can help someone else.

---

