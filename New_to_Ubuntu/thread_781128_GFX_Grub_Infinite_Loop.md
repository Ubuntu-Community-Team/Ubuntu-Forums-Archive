---
title: "GFX Grub Infinite Loop"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by figos on 2008-05-04
So basicaly I was installing GFX Grub in my laptop and when I came to this step:

> The last thing you have to do is to install Grub MBR .

    sudo fdisk -l

You will get an output like this

    Disk /dev/sda: 80.0 GB, 80026361856 bytes
    255 heads, 63 sectors/track, 9729 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes
    Disk identifier: 0×0dd6c6bd

    Device Boot Start End Blocks Id System
    /dev/sda1 * 1 3187 25599546 7 HPFS/NTFS
    /dev/sda2 3188 8287 40965750 f W95 Ext’d (LBA)
    /dev/sda3 8288 9607 10602900 83 Linux
    /dev/sda4 9608 9729 979965 82 Linux swap / Solaris
    /dev/sda5 3188 5737 20482843+ 7 HPFS/NTFS
    /dev/sda6 5738 8287 20482843+ 7 HPFS/NTFS

Look for the bold Entry and finally install MBR in Filesystem

    sudo grub-install /dev/sdaX
    Note : Replace sda by hda if it is in fdisk -l output

Instead of grub-installing on my "Linux" partition I was dumb enough to install it in my "sda1-HPFS/NTFS" equivalent which is my Windows Vista partition. So now everytime I boot to that partition a new GFXGrub selection menu logically comes up and I'm stuck in an infinite loop. I checked to see if there was a grub-uninstall equivalent but to no avail. How can I uninstall grub from this partition?

Sorry if this has already been posted but I searched and found nothing.

---

### Post by figos on 2008-05-04
Fixed With Windows Vista DVD

---

