---
title: "[SOLVED]Error to access external hard drive"
date: 2016-08-17
forum: New to Ubuntu
---

### Post by xedoc on 2016-08-17
Hello,

I've got this error when i try to access an external hard drive like a disk or an usb pen.

"Error mounting /dev/sda1 at /media/shinigami/UUI: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sda1" "/media/shinigami/UUI"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'"

I tried before to access to a hard disk formated with fat32, i thought fat32 would be accessible by any system, but i wasn't sure about linux so i formated to exfat. The same happens.

Kind regards,

---

### Post by yancek on 2016-08-17
You can read/write FAT32 and if you have ntfs-3g installed, read/write ntfs.  xfat is not common enough and you will have to install software to be able to use it.  See the link below for instructions.

[http://askubuntu.com/questions/451364/how-to-enable-exfat-in-ubuntu-14-04](http://askubuntu.com/questions/451364/how-to-enable-exfat-in-ubuntu-14-04)

---

### Post by xedoc on 2016-08-18
Hi Yancek,

Problem fixed by using one of the methods provided by the link. I'll put the fix here to help others.

"
I installed "Synaptic package manager", with it synaptic i installed "exfat-utils and exfat-fuse" 
"

Thanks for the help.

Kind regards,

---

