---
title: "ls syntax"
date: 2014-01-16
forum: New to Ubuntu
---

### Post by bc.haynes on 2014-01-16
I am trying to list the files in a folder on a usb stick. The folder is locked. The usb stick is sdc. This is ubuntu 12.04. I tried {sudo ls -l /dev/sdc/lost+found} . I get back "Could not access....There is no directory." What am I doing wrong?:(

---

### Post by spencer the great on 2014-01-16
/dev/sdc is a special block device file (hm, is that what it is called?) that refers to the usb stick, but the usb stick probably isn't its own partition.  This has nothing to do with ls, but rather, you need to mount the usb stick.
Start by making a mount point in your home directory (it doesn't  have to be in your home directory, but we'll put it there for convenience):
```
$ mkdir ~/mnt
```
As root, mount the usb stick into the folder:
```
$ sudo mount /dev/sdc ~/mnt
```

The usb stick is now MOUNTED to a folder called mnt in your home directory, meaning you can now see and edit the contents of your usb stick in the aforementioned folder.

To safely remove it, you need to UNMOUNT it as root:
```
$ sudo umount ~/mnt
```
(make sure you close all programs that are looking at the contents of your usb stick first, or it won't work)

EDIT: Oh, well, you could do what Habitual said, assuming the device is automatically mounted in Ubuntu and you can already see the contents of your stick

---

### Post by Habitual on 2014-01-16
```
mount | grep  sdc
```

```
ls -l /path/to/mount
```

example:
```
mount | grep sda1
/dev/sda1 on [COLOR=#ff0000]**/**[/COLOR] type ext4 (rw,commit=0)
sudo ls -l [COLOR=#ff0000]**/**[/COLOR]lost+found/
total 0
```

alternatively, you could
df -h and see the same "mounted on" and use that for the ls -l
with the drive plugged in of course.

---

