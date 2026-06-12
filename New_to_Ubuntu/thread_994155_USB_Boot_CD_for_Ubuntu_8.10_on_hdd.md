---
title: "USB Boot CD for Ubuntu 8.10 on hdd"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by pbennington on 2008-11-26
hi, 
im new to ubuntu ( i have xp installed as main op) and have succesfully installed it on a usb pen drive, unfortunatly my laptop doesn't have any usb boot options from the bios and so i have had to use the USB Boot CD for Ubuntu 8.10 to load usb drivers, my question is, is it possible to copy the contents of this cd to a new hdd partition and then create a boot menu with xp as first option and the boot cd as the second (which will load the usb drivers) and so no longer needing to rely on having the boot cd?

---

### Post by nhasian on 2008-11-26
it sounds like you might as well just install ubuntu onto the new partition.  you can still use the thumbdrive for storage if you like :)

---

### Post by cariboo on 2008-11-26
Have you tried a wubi installation? this will install Ubuntu inside windows, and then at bootup you will have the choice of booting XP or Ubuntu. The best alternative is letting Ubuntu resize you hard drive and install on a separate partition.

If you choose tho option of installing on a separate partition, make sure you run defrag at least twice before proceeding, and of course backup your important data before doing anything.

Jim

---

### Post by pbennington on 2008-11-26
hi
the reason i haven't installed ubuntu onto a partition on the hard drive is due to disk space as it's running a bit low and needs tidying up, a usb boot disk on the hdd would only require a small partition, i'm just not sure if it is possible? the other appealing thing about having an os on a usb stick is that i can build one for the other half and configure all her email etc, then when it all gets messed up my usb will still work :-)

---

### Post by Jose Catre-Vandis on 2008-11-26
Just done a howto on this, assuming you used the usb creator tool or pendrive linux instructions to install a "live cd" version to your flash drive.

[http://ubuntuforums.org/showthread.php?t=992426](http://ubuntuforums.org/showthread.php?t=992426)

but this relies on grub being installed on your hard drive

---

### Post by Jose Catre-Vandis on 2008-11-26
Just done a howto on this, assuming you used the usb creator tool or pendrive linux instructions to install a "live cd" version to your flash drive.

[http://ubuntuforums.org/showthread.php?t=992426](http://ubuntuforums.org/showthread.php?t=992426)

but this relies on grub being installed on your hard drive

---

### Post by caljohnsmith on 2008-11-26
> **pbennington said:**
> hi, 
im new to ubuntu ( i have xp installed as main op) and have succesfully installed it on a usb pen drive, unfortunatly my laptop doesn't have any usb boot options from the bios and so i have had to use the USB Boot CD for Ubuntu 8.10 to load usb drivers, my question is, is it possible to copy the contents of this cd to a new hdd partition and then create a boot menu with xp as first option and the boot cd as the second (which will load the usb drivers) and so no longer needing to rely on having the boot cd?
Yes, it's definitely possible to do what you want. I think the easiest way would be to resize your Windows partition to make a ~200 MB ext3 partition on your Windows drive; then reinstall Ubuntu to your USB drive, but during the installation set the mount point on on the 200 MB partition as "/boot", while your USB drive would have the root "/" file system. If you do it that way, you won't even need a boot CD; you will be able to boot Windows or Ubuntu from your Windows drive. Let me know how it goes or if you run into problems. :)

---

### Post by pbennington on 2008-11-27
> Yes, it's definitely possible to do what you want. I think the easiest way would be to resize your Windows partition to make a ~200 MB ext3 partition on your Windows drive; then reinstall Ubuntu to your USB drive, but during the installation set the mount point on on the 200 MB partition as "/boot", while your USB drive would have the root "/" file system. If you do it that way, you won't even need a boot CD; you will be able to boot Windows or Ubuntu from your Windows drive. Let me know how it goes or if you run into problems.


thanks for the info, would this method mean that the usb stick will only work on the laptop with /boot partition and not other computers (ubless they had a /boot partition)

cheers

---

### Post by caljohnsmith on 2008-11-27
> **pbennington said:**
> thanks for the info, would this method mean that the usb stick will only work on the laptop with /boot partition and not other computers (ubless they had a /boot partition)

cheers
Yes, using the exact method I described would mean the USB stick will only work with the laptop with the /boot partition; but if you want to use your USB drive on other computers and not make it dependent on your laptop for booting, you could simply copy over your /boot partition from the USB stick to the small 200 MB partition on your Windows internal HDD, install Grub to the MBR of the Windows internal HDD, and then you should be able to boot the USB stick from the Windows drive if all goes well. And the USB stick would still have it's own /boot directory, so you should be able to use it with other computers. Is that maybe what you are looking for?

---

