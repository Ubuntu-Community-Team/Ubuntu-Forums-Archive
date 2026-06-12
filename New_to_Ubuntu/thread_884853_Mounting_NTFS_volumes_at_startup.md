---
title: "Mounting NTFS volumes at startup"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by dave_didlydodo on 2008-08-09
I'm just moving over from XP to Ubuntu (Hardy), installed on an empty partition on my hard drive. However, all of my files (documents, pictures etc) remain on the old NTFS volumes. I can get to them ok, but how can I get Ubuntu to mount these volumes on startup?

---

### Post by perlluver on 2008-08-09
You will have to edit /etc/fstab.  So in a terminal type gksu gedit /etc/fstab.  Then type in /dev/sd? that being the hard drive you want to mount.  Followed by the mount point ie. /media/disk.  Then ntfs defaults 0 0.

So /dev/sd1 /media/disk ntfs defaults 0 0.

Also if you could post the output of sudo fdisk -l.  I could give you the hard drive you want.

---

### Post by pi.boy.travis on 2008-08-09
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=8a1da757-1c67-4394-aa10-57ba2bb8d8f0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=011b393e-9426-45d9-ab8b-75c4760af601 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Here is an example of my fstab.  Just create a new entry for the partition you want to mount automatically.  If you need help finding any of this information, you can find most of it by using GParted, which is a graphical partition editor.  If you don't already have it, you can install it with:

```
sudo apt-get install gparted
```

Hope this helps!

---

### Post by sisco311 on 2008-08-09
install ntfs-config from Synaptic, Add/Remove or the terminal :
```
sudo aptitude install ntfs-config
```Applications -> System Tools -> NTFS Configuration Tool

---

### Post by dave_didlydodo on 2008-08-10
Thanks guys.

I'll try ntfs-config first, and if I can't get that to work, then I'll edit fstab using data from gparted.

---

### Post by Joeb454 on 2008-08-10
> **dave_didlydodo said:**
> Thanks guys.

I'll try ntfs-config first, and if I can't get that to work, then I'll edit fstab using data from gparted.

It's incredibly easy to do. I wrote a HowTo on automounting NTFS drives (you can find the link in my sig) which uses [ntfs-config]("apt://ntfs-config")

---

