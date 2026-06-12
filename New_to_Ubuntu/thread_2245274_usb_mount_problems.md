---
title: "usb mount problems"
date: 2014-09-22
forum: New to Ubuntu
---

### Post by deepdarkhall on 2014-09-22
Been trying the hole day to create a startup disk. when i use "disks" i kan make a partition with my iso, its booable and should work. If i try startup disk creator it shows my drive as full with no extra space. I try to erase it but i doesnt work (left it fo a hour and when i came back it was still trying to erase it. the disk is 8 gb. I used it onse before with startup disk creator and it worked fine at that time! This is what comes up when I try to mount it!

Error mounting system-managed device /dev/sdb1: Command-line `mount "/mnt/sdb1"' exited with non-zero exit status 32: mount: block device /dev/sdb1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

 (udisks-error-quark, 0)

---

### Post by sudodus on 2014-09-22
Welcome to the Ubuntu Forums :-)

The ***Startup Disk Creator*** works well for me to create a USB boot disk (pendrive), but there is a bug, that prevents it from erasing the pendrive. So if you want to erase it, you must use another tool, for example ***gparted***.

You can also try another tool for making USB boot disks (pendrives), for example ***Unetbootin*** or ***mkusb***. I am right now finishing the development of mkusb version 9. See this link

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by snowmobiler on 2014-09-23
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

The ***Startup Disk Creator*** works well for me to create a USB boot disk (pendrive), but there is a bug, that prevents it from erasing the pendrive. So if you want to erase it, you must use another tool, for example ***gparted***.

You can also try another tool for making USB boot disks (pendrives), for example ***Unetbootin*** or ***mkusb***. I am right now finishing the development of mkusb version 9. See this link

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

I was having similar problems earlier. I didn't mention it in the other thread, but when I got my USB drive back to MBR and Fat32 formatted, the first time I tried to put the ISO on the stick, it copied the files, but the boot loader failed. So then I used SDC to erase the disk so I could try again and it worked.

---

