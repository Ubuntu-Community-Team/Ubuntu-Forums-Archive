---
title: "can i use this to install puppy linux on a flash card"
date: 2007-06-20
forum: Other OS Talk
---

### Post by zach12 on 2007-06-20
can i use this or do i have to mod it to get it to work
The following tutorial will show you how to install Knoppix 5.1.1 to a USB flash pen drive. It is also possible to use the persistent feature after completing this tutorial allowing you to save changes back to the stick. Knoppix is a fully featured Linux distribution based on Debain. It was created by Klaus Knopper. Knoppix has always been feature packed, including hundreds of useful tools and applications not included by default with most other Live Linux distributions.

USB Knoppix 5.1.1 Screenshot:

Knoppix running from USB

USB Knoppix installation essentials:

    * Knoppix 5.1.1 ISO
    * CD Recorder
    * 1GB or larger USB stick

Knoppix 5.1.1 USB Installation process:

   1. Download the Knoppix 5.1.1 ISO and burn it to CD
   2. Insert a 1GB or larger USB flash drive
   3. Restart your Computer and boot from the Knoppix CD
   4. Open up a terminal and type sudo su
   5. Type fdisk -l note which drive is your USB stick (I.E: sda) Throughout this tutorial we use x as our flash drive letter. Replace x with your actual flash drive letter. For example, if your flash drive is sdb, replace x with b.
   6. Type umount /dev/sdx1
   7. Type fdisk /dev/sdx
         1. type p to show the existing partition and d to delete it
         2. type p again to show any remaining partitions (if partitions exist, repeat step 7)
         3. type n to make a new partition
         4. type p for primary partition
         5. type 1 to make this partition one
         6. hit enter to use the default first cylinder
         7. type +750M to make the partition 750 MB
         8. type a to make this partition active
         9. type 1 to select partition one
        10. type t to change it’s file system
        11. type 6 to select the fat16 file system
        12. type n to make another new partition
        13. type p for primary partition
        14. type 2 to make this the second partition
        15. hit enter to use the default first cylinder
        16. hit enter again to use the default last cylinder
        17. type w to write the new partition table
   8. Type umount /dev/sdx1 to ensure the partition is unmounted
   9. Type mkfs.vfat -F 16 -n usb /dev/sdx1 to format the first partition
  10. Type umount /dev/sdx2 to ensure the partition is unmounted.
  11. Type mkfs.ext2 -b 4096 -L casper-rw /dev/sdx2 to format the second partition
  12. Remove and reinsert your USB flash drive
  13. Type mkdir /tmp/usb
  14. Type mount /dev/sdx1 /tmp/usb
  15. Type cd /cdrom
  16. Type cp -rf KNOPPIX boot/isolinux/* /tmp/usb
  17. Type cd /tmp/usb
  18. Type mv isolinux.cfg syslinux.cfg
  19. Type cd
  20. Type umount /tmp/usb
  21. Type syslinux -sf /dev/sdx1
  22. Reboot your computer and set your system BIOS to boot from USB-HDD. Also set the boot priority to boot the USB device first if this option is available.

You should now be able to boot Knoppix 5.1.1 via your USB stick and use the Knoppix Persistent feature to save your changes back to the stick ;)

thanks

---

### Post by smoker on 2007-06-21
hi, why bother with all that. puppy has it's own installer and you just select your medium, eg, flash drive, whatever, and follow the simple steps, should take no more than five minutes! to run the installer, load the puppy live cd, then right click for menu, and select the installer from the options available.

best of luck

---

