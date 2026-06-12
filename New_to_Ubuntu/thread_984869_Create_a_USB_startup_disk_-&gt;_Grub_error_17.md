---
title: "Create a USB startup disk -&gt; Grub error 17"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by petri on 2008-11-17
Installation to USB stick works fine but I can't start Ubuntu from stick because the Grub error 17. The error appears before I can do anything with Grub. I have even tried the Pendrivelinux way: [http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/) with same error. All 3 computers report the Grub error 17 so something simple must be wrong.

Before in this USB stick I hade Ubuntu 8.04 installed as an real harddrive but I can't find the howto to install Ubuntu in that way.

---

### Post by bobnutfield on 2008-11-17
I would recommend using [UNETBOOTIN]("http://lubi.sourceforge.net/unetbootin.html")

It is a GUI makes installing to a USB stick a snap.

---

### Post by C.S.Cameron on 2008-11-17
Usb-creator always seems to work for me after deleting the files from a Unetbootin install.
Or if you wish you can make a Unetbootin install persistent.

You can do a Full install to flash drive using the same method as to internal HDD. Boot from Live CD or Live USB and click install on the desktop.
(I suggest disabling your internal HDD first so you don't mess up it's MBR).
When you get to partitioning you can choose any of the three methods, use full disk, use remaining space or manual.
If you use remaining space or manual you can leave a little FAT32, (on the left side), so windows can see the flash drive.
For manual partitioning on a 4G drive, (minimum), 500 MB FAT32, 1 GB /home and 2.5 GB root, (/), is a good starting point and can be adjusted later using gparted.
Home and root can be formatted as ext3 or reiserfs.
This should make a flash drive that works just like a HDD install only a little slower at times.

---

### Post by aurelieng on 2008-11-17
That's funny: I did the same thing today, and have the same "Grub error 17" message upon boot.

@C.S.Cameron, I followed the procedure you decribed in your post:
1. unplug the internal hard disk for safety
2. boot on the liveCD (8.04.1, I want LTS)
3. partition the USB stick as follow:
```

Disk /dev/sde: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ec711

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1          92      738958+   b  W95 FAT32
/dev/sde2   *         585         983     3204967+  83  Linux

```
2. install ubuntu on the USB stick, no error, everything went fine
3. reboot

And all I have is a grub error 17.

To get rid of the error, I installed syslinux, which is working perfectly except that I have to specify manually the device to use as the root filesystem (/dev/sda2 in my case, since the stick is detected as /dev/sda upon boot). I guess this has to do with the fact that the initrd.img I am using is not the one of the liveCD, which may be able to identify the root filesystem by scanning all available partitions (am I right).

To be able to plug my Ubuntu's USB stick on any  computer, I guess I have to:
- modify the stock initrd to identify the root partition
- add the hardware detection scripts of the liveCD to the USB stick installation (especially for the X configuration)
- use a ramdisk for /tmp and /var to avoid too many read/write operations.

Do you have some advices, solutions, or urls to guide me ? :-)

Cheers,

Aurélien.

---

### Post by C.S.Cameron on 2008-11-17
With 8.04.1 I just run setup from the CD and it usually works.

I have had grub error 17, but think it was due to scratchy CD's or a dirty burner, But your file system sounds ok.

I assume you used manual partitioning in setup as I don't see swap, and that you set mount point for the ext3 linux partition as "/".

When you get to partitioning, have you tried "Guided use entire disk"?, I seldom use the last option in setup, Advanced, as it usually sets up grub in the right place by itself.

What does your menu.lst look like, is it showing root as (hd0,1)?

---

### Post by aurelieng on 2008-11-17
My filesystem seems OK... and you're right: no swap file, and the ext3 partition mounted as "/". The menu.lst shows root as hd (0,1), as expected.

Anyway, I finally managed to find a workaround to this mess: syslinux is now used instead of grub. Once Ubuntu has been installed on the stick, I mounted it to my computer, and did the same for the equivalent desktop live cd. Then, I followed the steps below (gathered in a single bash script, which has not been tested):

```

#!/bin/bash

# # # User defined variables # # #
# Prerequisite : apt-get install syslinux
CDMNT=/media/cdrom0     # desktop live CD mount point
USBDEVICE=/dev/sdc      # USB stick block device
USBMNT=/mnt/tmp2        # USB stick mount point
SYSLINUXPATH=syslinux   # should not be changed ?
LABEL=liveusb           # label of the root partition, on the USB stick, set w/ e2label
# # # End of user defined variables # # #

# Reset the MBR
cat /usr/lib/syslinux/mbr.bin > ${USBDEVICE}

# Copy isolinux from the desktop live CD
mkdir ${USBMNT}/${SYSLINUXPATH}
cp ${CDMNT}/isolinux/* ${USBMNT}/${SYSLINUXPATH}

# Generate an ad hoc extlinux.conf
echo "DEFAULT /vmlinuz" > ${USBMNT}/${SYSLINUXPATH}/extlinux.conf
echo "APPEND  initrd=/initrd.img ro root=LABEL=${LABEL} --" >> ${USBMNT}/{$SYSLINUXPATH}/extlinux.conf

# Install syslinux on the USB stick
extlinux -i ${USBMNT}/${SYSLINUXPATH}


```

---

### Post by petri on 2008-11-22
Installation to flash using it as an "real hard drive" worked after I disconnected the hard drives. Then I was able to choose USB as a boot device.

However disconnecting the hard drives does not help when "Create a USB startup disk" I still got the error 17.

Yes I'm aware of the different workarounds but I just want the menu alternative to work so I can show it to people how handy Ubuntu is :lolflag:

---

### Post by aurelieng on 2008-11-22
It is the liveCD menu that you are interested in ? If so, you can install syslinux as a bootloader, and use the syslinux.cfg file of the live cd :)

---

### Post by petri on 2008-11-23
Not specially, I'm just tired to workarounds in Ubuntu therefore I want the menu post "Create a USB startup disk" just work. I was hoping someone could point me what I have ignored/forgotten. 

I have tried to boot from Usb stick with all the internal drives unplugged and end upp with the same error 17. 

If error 17 means > 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB
[http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors](http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors)
then I wonder why doesn't grub recognize either fat32 or ext3.

The same USB stick works when it has a "real installation" on it.

---

### Post by petri on 2008-11-25
Finally I found out why I got the Grub error 17. It's because of the previous Ubuntu installation on the flash drive creates (of course?) an MBR which is not wiped out by "Create a USB startup disk". *usb-creator* kind of assumes that your flashdrive is a brand new.

At Launchpad I found this thread [https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/285713]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/285713") and that procedure helped me to wipe out the old MBR from the flash drive.


edit: *syslinux* was on my flash drive after the creation at the very first beginning so I really didn't understand why I should install that again.

---

