---
title: "format usb with gparted"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by flyingsolo on 2008-09-17
I seem to be stuck on something  kind of simple...I'm trying to create a bootable usb & have used gparted  to delete the drive & now want to format it (reformat it, really) but in gparted it appears as /dev/sdb and unallocated 7.5GB but I can't format it b/c the format option is greyed out.  It's probably a simple step but what am I missing?
Thanks.

---

### Post by Zzl1xndd on 2008-09-17
My best guess would be its still mounted. If it is unmount it and try to format it then.

---

### Post by flyingsolo on 2008-09-17
thanks, but, no, it doesn't seem to be mounted; in fact I unmounted it in order to delete it.  Now when I right click it, the only options available are 'New' and 'Information'.  (unmount option is also greyed out)

---

### Post by Zzl1xndd on 2008-09-17
Oh I see now, you deleted the partition table. Just select new and you should be able to recreate it and format it at the same time.

---

### Post by Dill on 2008-09-17
I've had trouble formatting and partitioning USB drives from GParted, as well. You might try booting into Ubuntu, opening a Terminal, and using dd to erase the drive, then fdisk to format...

First, (this is very important) find out the device file which corresponds to your USB drive...

```
sudo fdisk -l
```

Once you know that, substitute the correct file for "your_usb_drive" below. "dd" will overwrite your flash drive with a series of null characters, so it's important that you choose the correct device, just so you don't overwrite your hard drive. Alternatively, you can skip the "dd" code below and erase your USB drive from the GUI.

```
dd if=/dev/zero of=/dev/your_usb_drive
```

Then, you can use fdisk to format and partition the USB drive

```
fdisk /dev/your_usb_drive
```

This is a good guide on how to use fdisk:
[http://tldp.org/HOWTO/Partition/fdisk_partitioning.html](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html)

Good luck on getting GParted to work, but if it doesn't, hopefully this will!

Cheers, 
Dylan

---

### Post by C.S.Cameron on 2008-09-18
Just select new in gparted.
or manual when you get to partitioning at install.
I often format in windows and leave a little of the FAT32 partition when formatting during install, so that it will open when connected to a windows machine.

---

### Post by flyingsolo on 2008-09-18
Thanks--that did it; I guess I saw the 'Format' option greyed out & didn't look at recreating the partition first.  (see, I knew it was something simple!)

---

