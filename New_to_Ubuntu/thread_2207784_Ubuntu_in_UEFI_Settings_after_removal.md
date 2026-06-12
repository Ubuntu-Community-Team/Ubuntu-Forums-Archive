---
title: "Ubuntu in UEFI Settings after removal"
date: 2014-02-25
forum: New to Ubuntu
---

### Post by gurbinder2 on 2014-02-25
I intended to dualboot Ubuntu 12.04 on my Windows 8 laptop. But there where so many errors that I decided to install it in VirtualBox. But now my problem: I used EasyBCD to restore the MBR and then deleted the partitions but they did not turn green as they did in some instruction videos. And I have two Ubuntu entries in the UEFI settings and when I try booting one of them nothing happens so I am pretty sure that there is nothing left of Ubuntu but how do I get those entries out?

---

### Post by oldfred on 2014-02-25
Is this UEFI?
If UEFI, you have to coordinate removal from efi partition, UEFI NVRAM and BCD as each may update the other.

Similar issue.
[http://ubuntuforums.org/showthread.php?t=2207532](http://ubuntuforums.org/showthread.php?t=2207532)

       Query to see if UEFI or BIOS
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 


 Remove Duplicate Firmware Objects in BCD and NVRAM
[http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx)
UEFI NVRAM boot entries are cached in the BCD store
BCD has 1:1 mappings for some UEFI global variables
Any time {fwbootmgr} is manipulated, NVRAM is automatically updated

      
 # from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

---

### Post by gurbinder2 on 2014-02-25
Yes it says "UEFI enabled" in the "BIOS" settings.

---

### Post by Gordonbp531 on 2014-02-27
On my Lenovo, I go into BIOS settings at startup, go to the Boot tab, and delete the Ubuntu entry.
Try that.

---

