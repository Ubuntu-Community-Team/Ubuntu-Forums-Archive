---
title: "No Boot Device detected. Boot-Repair doesn't help."
date: 2017-01-24
forum: New to Ubuntu
---

### Post by balduin2 on 2017-01-24
I got a new Acer Travelmate Notebook and wanted to install Ubuntu or elementary OS.
I don't know what went wrong, but after installing the computer says "No bootable device".
Boot-Repair doesn't seem to work either. Here is the log: [http://paste2.org/pjPzd67Z](http://paste2.org/pjPzd67Z)
I also tried to reinstall GRUB but got this error: failed to get canonical path of /cow.
I would really appreciate some help, thanks in advance.

---

### Post by yancek on 2017-01-24
You have windows EFI files on the EFI partition as well as the Ubuntu EFI files.  You don't have any windows system partition.  Did you have some version of windows installed?  It's not there if it was, was that deliberate on your part?  Do you have the BIOS set to boot UEFI?  The Grub files seem correct as do the entries so other than setting the BIOS to EFI, I'm not sure what you could change.  Hopefully someone more familiar with UEFI will have a suggestion.  You might take a look at the options/settings for the Acer in the user manual if you have one.  Otherwise, they are usually available online.

---

### Post by oldfred on 2017-01-24
Acer is the only vendor that requires you to set a UEFI supervisory password & then enable "trust" on the ubuntu/grub .efi boot files in the ESP from with in the UEFI. Other brands even make it more difficult. Few are easy.
You may find some threads that mention downgrading UEFI from Acer. Other newer ones say to upgrade to very newest UEFI and that works.
So make sure you have newest UEFI from Acer. Some version of UEFI from Acer does not work.

       Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392
[/URL]
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 

[URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]
[/URL]

---

### Post by balduin2 on 2017-01-24
Thanks!
I followed the instructions on this page: [http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
After Ubuntu worked, I tried the same with elementary OS. But it didn't work, so I wanted to switch back to Ubuntu. But then I always had the GRUB menu while booting, where I had to select Ubuntu on every reboot.
So I reset the EFI settings in BIOS, deleted all partitions and reinstalled Ubuntu.
Strangely even with the instructions above it didn't work anymore. I got a BIOS message that there is no Boot volume to choose from.
So I switched to Legacy and it worked now. After a reboot I switched back to UEFI, selected the trusted file and now it finally works again.

---

### Post by oldfred on 2017-01-24
It now sounds like you have both BIOS/CSM mode working and UEFI boot mode working.
But after grub updates based on whatever mode you are in, that mode may then only be the one working.

Generally best to pick one boot mode and only use that for booting USB installer, actual install and any repair flash drives or DVDs.
UEFI has some advantages, but not significant at this point.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

