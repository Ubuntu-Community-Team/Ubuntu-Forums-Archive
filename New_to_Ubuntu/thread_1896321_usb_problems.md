---
title: "usb problems"
date: 2011-12-16
forum: New to Ubuntu
---

### Post by spillage2 on 2011-12-16
Hi all,

Running 10.04 and recently found that any data been moved via usb is failing. Everything starts ok but then has errors and refused to save from the comp to usb drives. Have now tried 5 pendrives and all the same..


spill.

---

### Post by Ms. Daisy on 2011-12-16
How many USB ports do you have on the computer? Have you tried them all?  Check if it's just one port or all of them.

---

### Post by BC59 on 2011-12-16
First option is to do this:

```
gksudo gedit /etc/default/grub
``` 

Change this line
> GRUB_CMDLINE_LINUX=””
With this
> GRUB_CMDLINE_LINUX=”acpi=force irqpoll”
Save and run
```
sudo update-grub
```

Then reboot.

As a second option you could reset CMOS/BIOS settings.

---

### Post by spillage2 on 2011-12-20
Ok I have looked into this a bit more as it really started to annoy me. It now seems that anything formated in gparted will not allow access to the drive although this was never a problem. 

Problem is that if I now format the drive to a fat partition my works windoz system wont pick up the drives???

Spill.

---

### Post by Ms. Daisy on 2011-12-20
Did you try what BC59 suggested?

---

### Post by oklokl on 2011-12-20
usb make -> bug..
Log out ->gparted Process 
NO-> start gparted

fdisk -l
/dev/sdc -> Target

umount /media/you_mount_system_usb

cd /media/ 
dir

or
umount /media/* 

dd if=/dev/zero of=/dev/sdc bs=512 count=1

mkfs.vfat /dev/sdc1  ->gparted loop -> bug usb.. fast Clean

and gparted start
mbr-> ms-dos Reset
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=209432&stc=1&d=1324408937[/IMG]
and fat32 
or fat16.. Clean

mount usb Partition

---

