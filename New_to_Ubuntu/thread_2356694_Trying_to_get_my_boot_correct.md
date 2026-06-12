---
title: "Trying to get my boot correct"
date: 2017-03-25
forum: New to Ubuntu
---

### Post by revision2 on 2017-03-25
I am attempting to install Ubuntu but it is still booting from the USB (Seagate 1TB HDD) and my laptop has a 1TB as well, I believe, could be wrong though. Iv been trying some things online by searching for my problem but I cannot figure it out, I kinda feel like it is an easy fix but im still trying to learn it. Iv used boot repair and it also didnt fix it but did give me this. [https://paste2.org/OPacFkjy](https://paste2.org/OPacFkjy)

---

### Post by yancek on 2017-03-25
I'm not sure what you've done or are trying to do but, your first 1 TB drive seems to have nothing on it but the Ubuntu installer and your second 1 TB drive has Ubuntu on the second partition and the first partition is the FAT32 EFI partition.  You have an EFI partition also with the Ubuntu EFI files and also have some windows EFI files but no other windows partitions.  Were you intending to overwrite the windows installation?  Have you tried changing the BIOS settings to boot from the second drive?  You might need to check the owners manual for the computer on how to boot from a second drive with EFI.

---

### Post by revision2 on 2017-03-25
Im just trying to get ubuntu to install without having to use my usb and I wanted have just ubuntu with no windows. When I go to the BIOS it only brings up the boot menu with just the usb option.

---

### Post by ajgreeny on 2017-03-26
> **revision2 said:**
> Im just trying to get ubuntu to install without having to use my usb and I wanted have just ubuntu with no windows. When I go to the BIOS it only brings up the boot menu with just the usb option.
I am confused; how do you intend to install Ubuntu if you do not use the USB?
I also note that by some means or other you have more than one version of the kernel in the Ubuntu that seems to be on sda1 which is where grub.cfg is at present. 
```
sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 477106 of /dev/sda1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys
```
That also does not make sense.

Which disk do you want to install Ubuntu to, sda or sdb?
Something has gone very wrong and I suspect you may need to start again.

See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) which may help you with figuring out what has gone wrong.

---

### Post by yancek on 2017-03-26
You need to explore the BIOS options more carefully.  Check the manual or post info on who the manufacturer is and someone may be able to help with changing the boot options.

It looks to me like you used some software to put the Ubuntu installer on your 1TB drive and you will probably need to create a new partition table on it before you will be able to use it.  You need to find some way to change boot priority and since you have Ubuntu installed EFI, there must be some options in the BIOS to set that.

---

