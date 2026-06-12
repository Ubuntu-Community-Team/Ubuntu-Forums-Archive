---
title: "Auto mounted usb drives in launcher"
date: 2013-11-21
forum: New to Ubuntu
---

### Post by wetsprocket on 2013-11-21
I can see my 3 usb drives have been auto mounted in the ubuntu launcher. How can I access these drives from the terminal? When I try to mount the drive, I get the following error. I can access my drive in the gui but I do not know where this drive is mounted to access it in the terminal.

"Mount is denied because the NTFS volume is already exclusively opened.

---

### Post by coffeecat on 2013-11-21
You certainly can't mount a drive that has already been mounted. To find the mountpoint of an already mounted USB drive:

1 - **terminal** - run this command:

```
mount
```

Near or at the bottom of the output will be the lines for the automounted USB drives. An example:

```
/dev/sdc1 on /media/username/UDISK type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
```

That was a flash drive formatted fat32 mounted on /media/username/UDISK where "username" would be your Ubuntu account name. With three drives, you would have to work out which was which from the three lines.

2 - **GUI** - simply click on the launcher icon for the USB drive you want the mountpoint for. When the Nautilus window opens press ctrl-l (that's lower-case L). The breadcrumb bar will change to an address bar with the path to the mountpoint helpfully already highlighted if you need to copy it.

---

