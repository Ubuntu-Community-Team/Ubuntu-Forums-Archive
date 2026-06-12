---
title: "[SOLVED] how do you format a usb flash drive?"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2008-11-23
i tried to do it on my own. even searching/looking at this forum with no help.

how do i format it to FAT32 with some simple clicks and how do i do it i the terminal?

---

### Post by hyper_ch on 2008-11-23
well, first you have to partition it and then you have to apply a filesystem...

in the gui you can do this with gparted
in the shell you can use "sudo fdisk /dev/NAME_OF_USBDEVICE" and then you you run "sudo mkfs.vfat /dev/NAME_OF_USBPARTITION"

---

### Post by cdtech on 2008-11-23
sudo mkfs.vfat /dev/"yourusbdevice"

---

### Post by shiningkenmonster on 2008-11-23
thanks guys, but how do i found out the part about "NAME_OF_USBPARTITION" or "YOUR device"

i tried to do it on my own, but i think its /media or i have no clue

---

### Post by cdtech on 2008-11-23
Use the command:
```
sudo fdisk -l
```
This will give you a list of the devices on your system, you should see something like /dev/sdc1 listed.

---

