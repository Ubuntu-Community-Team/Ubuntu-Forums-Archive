---
title: "problem with installation"
date: 2018-10-03
forum: New to Ubuntu
---

### Post by daveads on 2018-10-03
unable to install ubuntu on my laptop...........
```
error msg  //GRUB INSTALLATION FAILED
          
            The 'grub-efi-amd64-signed'package fialed to install into /target/. without the GRUB boot loader, the installed system will not boot. 
```

am not dual boot with window 10, just installing ubuntu only 

so am confuse i thought "grub is meant for those who want to dual boot or some thin"

---

### Post by oldfred on 2018-10-03
Grub is boot loader & boot manger (menu).  You have to have it.

UEFI or BIOS system? All systems in last 5 years or since Windows 8 released are UEFI.
Install in UEFi or BIOS boot mode?
UEFI want gpt partitioning.

Error is typically from those installing in UEFI boot mode and not having an ESP - efi system partition which is FAT32 with boot flag. UEFI suggests it be first partition, but does not have to be first, but should be near beginning of drive.

Post this from live installer:
sudo parted -l

---

### Post by daveads on 2018-10-14
Thanks

---

