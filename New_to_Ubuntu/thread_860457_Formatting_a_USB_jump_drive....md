---
title: "Formatting a USB jump drive..."
date: 2008-07-15
forum: New to Ubuntu
---

### Post by PHATSPEED7x on 2008-07-15
I don't see a opition for formatting it. How would I do this????

---

### Post by Kingsley on 2008-07-15
Install gparted and go on from there.

---

### Post by cdtech on 2008-07-15
Lets assume that /dev/sdc1 is your partition name for USB pen (you can find yours by typing on a command line: fdisk -l). To format the device, type the following command (Open a terminal and type the command)
$ sudo mkfs.ext3 /dev/sdc1

Now use e2label command to change the filesystem label on the ext3 filesystem located on device /dev/sdc1:
$ sudo e2label /dev/sdc1 usb-pen

You can also create an MS-DOS/Windows XP file system under Linux, enter:
$ sudo mkfs.vfat /dev/sdc1

Now your ready to use the USB pen drive.

Hope this helps.........

---

### Post by PHATSPEED7x on 2008-07-15
Ok got it. Thanks.

---

