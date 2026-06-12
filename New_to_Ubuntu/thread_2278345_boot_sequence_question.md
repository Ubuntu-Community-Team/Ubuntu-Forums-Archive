---
title: "boot sequence question"
date: 2015-05-15
forum: New to Ubuntu
---

### Post by palmgrower on 2015-05-15
I am putting together a new desktop with a Pentium CPU, Z97 motherboard and DDR3.  I need to set up boot sequence. Of "hard disk" and "UEFI hard disk" which should I choose? What is uefi? I read wiki but all are about Windows 8. Thanks.

---

### Post by grahammechanical on 2015-05-15
It all depends on whether the motherboard has a BIOS boot system or a UEFI boot system. Basically, the boot system (BIOS/UEFI) is an integrated circuit which stores a program that tells the computer about the hardware in the machine.

If we have more than one hard disk we can set which hard disk to boot from. We can set which devices to search for an operating system and in which order to do the searching. We can do a lot of other stuff as well. You will need to study the motherboard user guide to find out about all that.

If there is going to be only one operating system on that machine then it will be less complicated than if there were more than one. Basically, the boot system (BIOS/UEFI) needs to be adjusted to look for an operating system first on a DVD drive or a USB port and then on the hard disk. Otherwise we cannot install the OS. Once the OS is installed and we shut down the computer and remove the DVD or USB memory stick and then restart the machine will look to the DVD/USB drive for an OS and not finding one will then look to the hard drive for an OS and finding the Boot loader that is installed on the hard drive proceed to follow the instructions of the boot loader.

BIOS = Basic Input Output System. UEFI = Unified Extensible Firmware Interface. Firmware = hardware = the opposite of software.

Regards

---

### Post by oldfred on 2015-05-15
UEFI is the new replacement for BIOS. BIOS has been around since early 1980's and cannot support all the new hardware & software features.
But then UEFI is more complex and has more settings that you may have to change. 
Currrent versions of UEFI have CSM which is an extra chip.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

UEFI also uses the newer gpt partitioning system. Again MBR(msdos) is old and cannot support drives over 2TiB. 

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

    
Some more info in the link in my signature.

---

### Post by palmgrower on 2015-05-15
Thanks for the notes. UEFI seems to be more than I can bite. I will select non-UEFI devices. If I will miss a lot by not selecting UEFI, please advise.

I have one OS, one hard drive, one partition,  one CD/DVD drive. I just want a working PC. Apparently, motherboard has UEFI setup. Otherwise I wouldn't have UEFI option. Thanks.

EDIT: Of 2 boot devices, CD/DVD drive was auto-recognized as UEFI CD/DVD drive and hard drive was not. In bios, I changed boot sequence to 1) UEFI CD/DVD drive and 2) UEFI hard drive. During Ubuntu 15.05 installation, I was prompted to accept UEFI hard drive setting (not exact words but sufficient explanation). No need to be afraid. I am glad I accepted the newer technology without adequate understanding. Thanks.

---

