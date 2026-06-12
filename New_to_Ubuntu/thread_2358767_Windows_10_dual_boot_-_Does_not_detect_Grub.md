---
title: "Windows 10 dual boot - Does not detect Grub"
date: 2017-04-17
forum: New to Ubuntu
---

### Post by jossygeorge on 2017-04-17
I bought a new PC recently. My motherboard seems to support both UEFI and Legacy and is currently set to use both. I am using MSI Click BIOS. I installed Windows 10 first and later tried to install Ubuntu using the 'Install alongside Windows option.'. After that, Grub would not detect Windows 10. I did a reinstall of Windows 10 and after the installation the Windows installer detected my old Windows. Now whenever I boot it goes straight to windows by-passing Grub. And Windows gives me the option to choose between the my old and new windows. I tried removing the new windows by formatting that drive(as it was on a second drive) but I still get the option during boot. Below I have attached my boot information using the Boot repair tool.

What I want is:
   - Have just two OS options in the beginning: Windows 10 and Ubuntu with Windows 10 as default

[https://pastebin.com/52hQHkRg](https://pastebin.com/52hQHkRg)

---

### Post by jossygeorge on 2017-04-17
I am guessing that I need to disable Fast Start up, then let boot repair move ubuntu to legacy(MBR)?

---

### Post by ajgreeny on 2017-04-17
Yes, you **must disable faststart** in the BIOS/UEFI settings or you will have big problems.  I also suggest that you disable secure boot if it is enabled at the moment.

You do not have grub installed in the MBR of sda at present which is why you can not boot Ubuntu and that should be spomething that is recoverable with Boot-Repair; if you choose the Advanced option there is, I believe, a chance to install grub though I have never needed to use it so have no personal experience.

---

### Post by oldfred on 2017-04-17
You booted the Boot-Repair in UEFI mode. Reboot in BIOS mode and Boot-Repair should offer to install grub2's boot loader to MBR. If more than one drive do not use auto fix as that installs grub to every MBR, but use advanced mode and choose install and choose drive's MBR.
But drive is MBR with BIOS boot configuration.

With BIOS you can only boot from the MBR or first sector of hard drive which is before first partition. You still have Windows boot loader in MBR.
If when you installed and this drive was not sda, then grub may have been installed to whatever drive was seen as sda. You have to use Something Else when you have multiple drives and want to control which drive's MBR gets boot loader.

       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

       
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

### Post by jossygeorge on 2017-04-18
Thanks guys. I disabled startup and booted to the live disk in legacy and ran boot-repair again. My problem seems to have been solved by the auto-fix. Here are the results: 

Boot-Info after doing the above - [https://pastebin.com/ATZS7Qst](https://pastebin.com/ATZS7Qst)

Boot-Info after auto-fix - [https://pastebin.com/4FqRfzmy](https://pastebin.com/4FqRfzmy)

---

