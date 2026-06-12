---
title: "Is there any benefit in using UEFI GPT instead of Legacy MBR?"
date: 2019-05-30
forum: New to Ubuntu
---

### Post by debofsky on 2019-05-30
[COLOR=#242729][FONT=Arial]Is there any benefit in using UEFI GPT instead of Legacy MBR?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Many thanks in advance![/FONT][/COLOR]

---

### Post by oldfred on 2019-05-30
[https://askubuntu.com/questions/1147508/is-there-any-benefit-in-using-uefi-gpt-instead-of-legacy-mbr](https://askubuntu.com/questions/1147508/is-there-any-benefit-in-using-uefi-gpt-instead-of-legacy-mbr)

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)
UEFI/BIOS gpt/MBR explanation - see post by Rod Smith
[http://askubuntu.com/questions/500359/efi-boot-partition-and-biosgrub-partition](http://askubuntu.com/questions/500359/efi-boot-partition-and-biosgrub-partition)

You have to have gpt with drives over 2TiB. And UEFI really should be gpt. Windows requires gpt with UEFI boot. Ubuntu will let you install to MBR, but probably should not let that happen.
The only place MBR is still required is Windows with BIOS boot.

All hardware since Windows 8 released in 2012 is UEFI as Microsoft required it to be installed in UEFI/gpt mode.
Most Windows 7 systems are installed in BIOS/MBR mode, but can be installed in UEFI mode.

I started converting drives to gpt with Ubuntu install in 2010. Then every new or totally repartitioned drive has been converted to gpt, even larger flash drives. Honestly cannot say I notice any difference. But some with MBR have had major issues that a backup gpt partition table would have made easy to resolve.

---

