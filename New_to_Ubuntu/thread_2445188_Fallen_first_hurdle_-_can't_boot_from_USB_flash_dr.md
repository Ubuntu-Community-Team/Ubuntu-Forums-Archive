---
title: "Fallen first hurdle - can't boot from USB flash drive"
date: 2020-06-10
forum: New to Ubuntu
---

### Post by billy102 on 2020-06-10
Trying to install Ubuntu for first time on HP Compaq 8200 Elite machine with windows 7. Old machine. Intel i5-2500. BIOS is listed as J01 v02.29. Machine boots to Windows.

Have downloaded Ubuntu 20.04, 18.04 and 16.04 to USB and to DVD. Cannot boot to any of them.

In BIOS I have changed the boot order. Have tried two different USB sticks. One returns 'disk error'. In all other cases WIndows boots.

Have read a couple of discussions about chaning BIOS settings but I cnanot find any of the items mentioned. BIOS looks up to date.

Any suggestions much appreciated

---

### Post by CelticWarrior on 2020-06-10
Welcome.

[https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview)
[https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview)
[https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview)

And if you really want to use optical media in 2020:
[https://ubuntu.com/tutorials/tutorial-burn-a-dvd-on-ubuntu#1-getting-started](https://ubuntu.com/tutorials/tutorial-burn-a-dvd-on-ubuntu#1-getting-started)
[https://ubuntu.com/tutorials/tutorial-burn-a-dvd-on-macos#1-overview](https://ubuntu.com/tutorials/tutorial-burn-a-dvd-on-macos#1-overview)
[https://ubuntu.com/tutorials/tutorial-burn-a-dvd-on-windows#1-overview](https://ubuntu.com/tutorials/tutorial-burn-a-dvd-on-windows#1-overview)

Please compare what you did with the above instructions. Redo if necessary. Make sure the BIOS is booting from the external media.

---

### Post by tea for one on 2020-06-10
Also, to access the HP boot selection, you need to press F9 as the PC powers on.

---

### Post by Autodave on 2020-06-10
Did you just copy the files onto your medium?  They need to be "installed" as an .iso.

---

### Post by billy102 on 2020-06-10
thanks. went through steps again and now working

---

### Post by C.S.Cameron on 2020-06-10
**There are many reasons a persistent USB might not boot.**

**BIOS**

- USB not set as first hard drive in BIOS

- Problems with BIOS or UEFI boot partitions or files.

- Secure Boot is not turned off

- Drive not compatible with computers BIOS or UEFI boot mode

- Incorrect partition table

- Out of date BIOS/UEFI firmware

- Junk in volatile memory

- Fstab entry in Full install USB referring to HDD's efi boot partition on drives created on uefi machines.

**GRUB**

- Incorrect root partition in grub

- Incorrect path to ISO in grub

- Incorrect persistent-path, (if used), in grub

- Grub menu entry structure not suiting OS

- Incorrect file type for vmlinuz and initrd (.efi and .lz)

- The word "persistent" is missing from grub.cfg, txt.cfg, syslinux.cfg or text.cfg

**Persistence (casper-rw and home-rw)**

- Persistence partition is not an ext filesystem 

- Persistence file not on FAT filesystem

- Persistence file/partition reused from different version

- Persistence file full of data, or file update attempted

**Hardware**

- Corrupted flash drive, reformat and reload

- Bad flash drive

- Not enough RAM to run Ubuntu

- Bad or incorrect USB socket

- Incompatible computer CPU

- Incompatible computer GPU

- Computer does not meet minimum specs, a lighter version of 'buntu is required

- Motherboard voltage irregularities

- Motherboard BIOS limitation with multiple USB devices

**Software**

- Bad MD5SUM / corrupt ISO file

- Modified or corrupted ISO9660 partition

- USB was removed from computer before ISO file is completely copied

- Out of date boot drive creation tool

- User inexperienced with boot procedure

---

