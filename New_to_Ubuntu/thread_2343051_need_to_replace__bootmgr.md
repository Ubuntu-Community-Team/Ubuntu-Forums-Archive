---
title: "need to replace  bootmgr"
date: 2016-11-12
forum: New to Ubuntu
---

### Post by jaxom98 on 2016-11-12
The old computer is failing, both mobo and hard drive,  so I got a 2nd hand computer to replace it (about 18 months old).
Old comp used bios mobo and was easy to dual boot.
New comp has uefi mobo. Had a computer shop set it up as I couldn't.
Layout is 1x ssd 320Gb dual booted with Edubuntu 14.04 and Win7 ult.
 1x1Tb hdd taking edubuntu data
1x500Gb hdd taking win7 data.

Problem
I removed old hdd from old computer   and plugged into new computer,(disconnected ssd with OS first) and tried to access win7 OS on old drive as old computer mobo has a fault that crashes win7 ,preventing start up. Unable to start win7 on new computer either. 
removed old hdd and plugged ssd.
On starting the new computer ,the error message: BOOTMGR is missing 
                                                                        Press Ctrl + Alt + Del to restart
Why would swopping hdd loose bootmgr?  I have swopped hdd's before without trouble.

---

### Post by oldos2er on 2016-11-12
Possibly because UEFI is looking for an efi partition which doesn't exist on the older disk. If you have or can get an external USB enclosure for it, replace your SSD, boot either Windows or *buntu, and attach the older disk with a USB cable to retrieve your data.

---

### Post by oldfred on 2016-11-12
New system is UEFI with CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

So you have to boot a system/drive in mode it was installed. Trying to boot a BIOS system with UEFI or vice-versa will fail.

And UEFI forgets it internal NVRAM settings for UEFI boot if you disconnect a drive. Most will find the .efi files in the ESP - efi system partition and add those back into UEFI boot menu. But many only find the Windows entry, some find the fallback or /EFI/Boot/bootx64.efi. And only a few find the Ubuntu entry. 
You may have to UEFI entries with efibootmgr. 

And Windows in BIOS mode has a separate 100MB boot partition with bootmgr & BCD. Are those still on drive for BIOS boot?

      
 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by jaxom98 on 2016-11-15
Hello oldos2er and oldfred, please excuse the delay in reply. In essence I will need a professional as I am out of my depth and will break things worse if I meddle. Thank you for identifying what went wrong.
I have swopped hdd's before, but only on older machines
Thank you for your time.

---

### Post by oldfred on 2016-11-15
If you run the Summary Report from Boot-Repair we can give specific commands or suggest what the Windows issues are, so you can ask correct question on a Windows forum, if we do not know details.

---

