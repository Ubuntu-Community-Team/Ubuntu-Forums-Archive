---
title: "grub not finding normal.mod"
date: 2015-06-12
forum: New to Ubuntu
---

### Post by Joshua5526 on 2015-06-12
Hi Guys,
Ubuntu Xen server was unresponsive this morning.  After trying to reboot it, it complains that it is missing the normal.mod file.  I searched the error message and found this article which contains the same error message: [http://askubuntu.com/questions/266429/error-file-grub-i386-pc-normal-mod-not-found](http://askubuntu.com/questions/266429/error-file-grub-i386-pc-normal-mod-not-found)
From this I learned that I need to fix/reinstall grub.  I then found this page telling how to install or repair grub
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
It pointed me to the boot-repair utility
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
I had a Kubuntu live disk on hand, I booted it, installed boot-repair and ran it.  It said it fixed the system and gave me a paste url: [http://paste.ubuntu.com/11701739/](http://paste.ubuntu.com/11701739/)
However when I reboot the system it still has the same error message about missing the normal.mod file.  I could go on messing with this and trying different ways to repair the disk, but the boot-repair page suggested it was best to ask for help first here before trying anything else.
~Joshua

---

### Post by Joshua5526 on 2015-06-12
Ok, guys.  After further thinking about it, I am just going to reinstall the OS.  The data files are on a secondary hard-drive and I took careful notes as to what I did when I set it up to begin with.  This also gives me a chance to update.
Thanks,

---

### Post by oldfred on 2015-06-12
Is this an older system with new large drives? Some older systems do not like to boot from files beyond 137GB on drive. I always have suggested and use smaller / (root) of 25GB and rest of space as /home or what I use /mnt/data for all the data I have. But then all of / is inside the first 137GB. Same type of issue has occurred with some newer systems booting from USB. But not on any new system with UEFI.

Each of your hard drives is at the limit of MBR(msdos).
If totally reinstalling you may want to think about starting to convert drive(s) to gpt partitoning.
Gpt has some advantages, but if using gpt you can only boot Windows using UEFI. But I had gpt for Ubuntu on one drive and MBR for my old XP on another drive and booting in BIOS Mode. Then I was able to move a gpt drive to my new UEFI based system.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

