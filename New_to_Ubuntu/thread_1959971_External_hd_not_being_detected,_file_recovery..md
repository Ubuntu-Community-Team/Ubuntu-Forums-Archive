---
title: "External hd not being detected, file recovery."
date: 2012-04-16
forum: New to Ubuntu
---

### Post by ihlinuxdude on 2012-04-16
Hi All.
I have a verbatim 320 gb portable HD that my system mysteriously decided not to detect anymore.
When I terminal lusub I get :
[B]Bus 001 Device 017: ID 18a5:0225 Verbatim, Ltd 
[/B]So ubuntu is seeing it on some level, but thats as far as my abilities go.
The part that really sucks is that this drive IS my backup and I just did a clean install on my laptop and had not taken the time to shift everything over. :cry::rolleyes:
Little help please?

---

### Post by dniMretsaM on 2012-04-16
What's the output of this:
```
sudo fdisk -l
```

---

### Post by ihlinuxdude on 2012-04-16
[FONT=monospace]Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00041c23

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   617283583   308640768   83  Linux
/dev/sda2       617285630   625141759     3928065    5  Extended
/dev/sda5       617285632   625141759     3928064   82  Linux swap / Solaris

Disk /dev/mapper/cryptswap1: 4022 MB, 4022337536 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xab95e508

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a266f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048      499711      248832   83  Linux
/dev/sdc2          501758   625141759   312320001    5  Extended
/dev/sdc5          501760   625141759   312320000   83  Linux

[/FONT]

---

### Post by dniMretsaM on 2012-04-16
/dev/sdc looks like your backup drive (same size, and it appears to be a USB device). Try mounting like this:
```
sudo mkdir /media/Backup1
sudo mkdir /media/Backup2
sudo mount /dev/sdc1 /media/Backup1/
sudo mount /dev/sdc5 /media/Backup2/
```

You can then access those partitions through your favorite file browser.

---

### Post by ihlinuxdude on 2012-04-16
Ok, just to be clear it's not an actual backup image, just my copies of stuff.
It's asking me for file system type when I use the last two commands.

---

### Post by dniMretsaM on 2012-04-16
Do you know what type it is? EXT4? Btrfs? NTFS?

---

### Post by ihlinuxdude on 2012-04-16
I'm not sure, is there a way to check?
I don't think I've ever formated it, I assume it's ntfs.  
What would be  the syntax to tell it what file-system it is?

---

### Post by kurt18947 on 2012-04-17
I assume this is a USB device?  Does it have a Y cable?  I have a spare hard drive in a cheap enclosure, only has a single plug.  It mounts and works well in some USB ports, doesn't work in others.  I assume because the disk electrical requirement is right at the 500 ma capacity of a single USB port.

---

### Post by callmemahavir on 2012-04-17
Execute the following command to find the file system type...

sudo file -sL /dev/sdc1

and for also all other device.

You will get the file system type.

---

### Post by dniMretsaM on 2012-04-17
> **ihlinuxdude said:**
> I'm not sure, is there a way to check?
I don't think I've ever formated it, I assume it's ntfs.  
What would be  the syntax to tell it what file-system it is?

It's a Linux file system according to the fdisk output. Chances are it's ext4. But run the command suggested by callmemahavir.

---

### Post by ihlinuxdude on 2012-04-17
> **kurt18947 said:**
> I assume this is a USB device?  Does it have a Y cable?  I have a spare hard drive in a cheap enclosure, only has a single plug.  It mounts and works well in some USB ports, doesn't work in others.  I assume because the disk electrical requirement is right at the 500 ma capacity of a single USB port.

Yeah, it's only one usb plug, but I''ve had it over a year and it's worked very reliably.

---

### Post by ihlinuxdude on 2012-04-17
Ok now sudo fdisk -l is showing the device to be sdb instead of sdc.
so when I run the command...
sudo file -sL /dev/sdb1 
/dev/sdb1: ISO-8859 text, with very long lines, with no line terminators

sudo file -sL /dev/sdb2
/dev/sdb2: x86 boot sector; partition 1: ID=0x83, starthead 59, startsector 2, 624640000 sectors, extended partition table (last)\011, code offset 0x0

sudo file -sL /dev/sdb5
/dev/sdb5: data

:confused:

---

### Post by dniMretsaM on 2012-04-17
That doesn't really matter. the device names change sometimes. What is the output of the command that callmemahavir suggested?

---

### Post by ihlinuxdude on 2012-04-17
sudo file -sL /dev/sdb1 
/dev/sdb1: ISO-8859 text, with very long lines, with no line terminators

sudo file -sL /dev/sdb2
/dev/sdb2: x86 boot sector; partition 1: ID=0x83, starthead 59, startsector 2, 624640000 sectors, extended partition table (last)\011, code offset 0x0

sudo file -sL /dev/sdb5
/dev/sdb5: data

---

### Post by ihlinuxdude on 2012-04-26
Can I use something like ddrescue or photorec, as is?
Can anyone walk me through it?

---

### Post by ihlinuxdude on 2012-04-27
BUMP!
Come on guys, I am lost here.  I am in uncharted territory, can someone help me through here!
I've got to get these files and pictures back!

---

### Post by ihlinuxdude on 2012-04-27
I have also taken my HD out of it's case and hooked it to a sata rig, so power is no longer the issue for sure.
Still not detected by the GUI.

---

