---
title: "How do I automount at startup??"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2008-10-11
I have 2 NTFS drives which I want to automount at startup.
I think I have to add something to fstab but I have no idea what to add.

Heres my current fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=c4668640-20c8-463a-bd8c-36243eabff09 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=f462f4f7-f404-4e14-a1ed-250adfc79396 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```

Any help would be greatly appreciated

---

### Post by sokopok on 2008-10-11
You could add to your /etc/fstab :
```
/dev/device /media/mountpoint ntfs defaults 0 0
```"/dev/device" is the disk you want to mount (eg. /dev/sda1), use a partition editor to find out which devices are your ntfs drives (eg. gparted).
"/media/mountpoint" is the folder where you want to mount the disk. This folder needs to exist before you mount the disk so create it first.
You need to be root to make modifications to your /etc/fstab, so use (gui) ```
gksudo gedit /etc/fstab
``` or (in a terminal) ```
sudo vim /etc/fstab
``` to start gedit/vim with root permissions.

When you made your modifications,  mount all drives like this: ```
mount -a
```Next time you reboot the drives will be mounted automagically.

For more options in /etc/fstab check: ```
man fstab
``` and/or ```
man mount
```Hope this helps.

---

### Post by bumanie on 2008-10-11
Ensure you have ntfs-3g installed (should be by default in 8.04), then install ntfs-config > sudo apt-get install ntfs-configGo to Applications --> System Tools --> Ntfs configuration tool. Fill in the window for both your ntfs drives and they will automatically be added to /etc/fstab and should automount.

---

