---
title: "Help Removing Ubuntu Partition"
date: 2013-03-13
forum: New to Ubuntu
---

### Post by Mortarius on 2013-03-13
I recently gave Ubuntu a try, but I've decided for now that I would like to just stick with Windows 7. I did the Ubuntu install that required me to download the installer and burn it to a disk. During the install I gave Ubuntu 250GB of HD space and Windows 7 the other 250GB of space. I was trying to Google how to remove Ubuntu from my computer after this manner of installation and most say just use the Windows 7 disk (My pc was not shipped with a disk, I do however have a Recovery partition?). I don't want to lose all of the stuff on my Windows 7 partition, but I want to have the computer back the way it was before having Ubuntu.

Thanks.

---

### Post by zrdc28 on 2013-03-13
There is an easy way to do this, download gparted, burn to cd.  Boot gparted delete the "right click on the partician" ubuntu partician and swap space. Now right click on the 
ntfs partician and "resize/move" . Now you have the 500gb back for windows. Personally I would delete the windows partician and use ubuntu.

---

### Post by arpanaut on 2013-03-13
With this tool you will be able to restore the win bootloader, then you can go about deleting the Ubuntu partitions and resizing your disk to original size.  Back up your important data first as any partition changing can go wrong. 

Boot Repair: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by fantab on 2013-03-13
You can just reformat the Ubuntu installed partition. To do this you can use your Ubuntu LiveCD/DVD/USB and utilize the Gparted utility. However you may have to repair your Windows or use recovery partition to fix it. The reason is, the Ubuntu boot loader will have overwritten your Windows Boot loader, and needless to say, Windows will not boot without its boot loader. Use this [Utility ]("https://help.ubuntu.com/community/Boot-Repair")to fix your Windows BOOT.

In case you find yourself unable to fix the Windows Boot loader issue, I would like to suggest that you keep the Ubuntu install. Install Ubuntu on a small 15-20 GB partition and only use "/" as your mountpoint, no need of "/home". And create a small swap of about 2-4GB. (If you follow this then remember you can have only FOUR Primary partitions on your HDD. If you need more you need to create an Extended Partition).

Good Luck...

---

### Post by Mortarius on 2013-03-13
Actually after thinking it over for a bit, I would like to keep Ubuntu on the computer as I may have more time to delve into it some more soon. Is there a simple way to change the partition sizes? I only want Ubuntu to have about 30GB and the rest for my Windows 7.

---

### Post by Mark Phelps on 2013-03-13
> **zrdc28 said:**
> There is an easy way to do this, download gparted, burn to cd.  Boot gparted delete the "right click on the partician" ubuntu partician and swap space. Now right click on the 
ntfs partician and "resize/move" . Now you have the 500gb back for windows. Personally I would delete the windows partician and use ubuntu.

Strange advice when the poster clearly said:

> I don't want to lose all of the stuff on my Windows 7 partition, but I want to have the computer back the way it was before having Ubuntu.

---

### Post by Mark Phelps on 2013-03-13
> **Mortarius said:**
> Actually after thinking it over for a bit, I would like to keep Ubuntu on the computer as I may have more time to delve into it some more soon. Is there a simple way to change the partition sizes? I only want Ubuntu to have about 30GB and the rest for my Windows 7.

You can shrink the Ubuntu partition by booting from an Ubuntu LiveCD or LiveUSB and running gparted.  It will probably take a while, as GParted is slow, but that should work.

Then, do NOT use GParted to expand the size of Win7; instead, boot into Win7 and use the Disk Management utility to do that.  Using Linux utilities on Win7 OS partitions runs the risk of corrupting them.

Also, once you get back into Win7, consider using the Backup feature to create and burn a Win7 Repair CD.  IF you decide later you want the Windows boot back into the MBR, you can easily do that by booting from this Repair CD.

---

### Post by LynNicks on 2013-03-13
You can just simply delete the Ubuntu partition using the default Windows Disk Manager. However it will ruin your bootloader, and you will have to fix it either before you turn off your computer (using EasyBCD) or at next bootup. (Using some sort of bootable bootloader fixer.)

---

