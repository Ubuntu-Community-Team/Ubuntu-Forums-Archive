---
title: "ubuntu wont boot without the cd after install"
date: 2013-05-19
forum: New to Ubuntu
---

### Post by David593 on 2013-05-19
I decided to give ubuntu a try and chose to replace windows with 13.04. After the install i removed the disk and restarted  and it says there's no boot disk or that it's a defective disk. When i put the cd back in and restart it, it boots and starts ubuntu. I've checked the boot priority and  installed boot-repair  successfully, but it still won't but without the cd.   The system is a gateway win8 desk top that's about 5 hours old and worked fine before the install. Any help would be very much appreciated. Thanx.

---

### Post by jamesisin on 2013-05-19
You are booting in the LiveCD.  That is a full installation of Ubuntu but it lives on the CD.  From within that LiveCD you can choose to *install* Ubuntu onto your HDD.  After you have completed that, you will be able to boot directly to Ubuntu from your HDD without the CD.

---

### Post by Kevin McCready on 2013-05-19
There may have been a failure during install.
Is it worth installing again?

---

### Post by David593 on 2013-05-19
Did an erase and reinstall. Still the same problem.

---

### Post by jamesisin on 2013-05-19
If you hold down shift (or esc depending) you will get to the grub boot menu.  Does that happen?  What do you see?

---

### Post by David593 on 2013-05-20
It brings up a list of installation options... Try ubunti without installing, install, oem install, check disk.

---

### Post by David593 on 2013-05-20
I typed: sudo fdisk -l in the terminal and got this -

  ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x9093115c

   Device Boot        Start                                     End                   Blocks          Id      System
/dev/sda1                                   1           976773167      488386583+      ee               GPT
Partition 1 does not start on physical sector boundary.
ubuntu@ubuntu:~$

---

### Post by David593 on 2013-05-20
Ok I made a bootable thumb drive from a new download and installed it and fixed the grub and I can boot without the usb or cd now.  But, I have to press F12 to get into the boot menu and choose between booting from the hdd or ubuntu

---

### Post by jamesisin on 2013-05-21
Try running *sudo update-grub* from a terminal.

---

### Post by oldfred on 2013-05-21
Your f12 is a one time boot key.
You should be able to go into UEFI/BIOS and change boot order to boot ubuntu first. So then it will be the default.

---

### Post by David593 on 2013-05-23
LOL, Well I feel like a real dummy. there's two list in bios one for boot order then another for priority. Ubuntu didn't show in boot order but I found it in priority and made it first... after that it appeared in the boot order list too.  Many thanx everybody.

---

