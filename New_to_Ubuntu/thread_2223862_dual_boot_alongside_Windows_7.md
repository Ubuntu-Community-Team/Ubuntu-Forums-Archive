---
title: "dual boot alongside Windows 7"
date: 2014-05-13
forum: New to Ubuntu
---

### Post by Robert_Grindstaff on 2014-05-13
I've seen other threads similar to this, but I suspect my issue may be different. I have Windows 7 installed on an HP laptop that originally came with Windows 8.  I'm wondering if the issues I'm having Matt be related to the BIOS our BIOS setup. With installing Ubuntu, the only option I get is a manual install... And I can't seem to successfully do that, though I believe I've followed tutorials correctly. I was able to install, but then couldn't access Windows 7. If someone might have some direction they could give, it would be greatly appreciated.

---

### Post by veddox on 2014-05-13
Could you give some more details? Especially in terms of the partitions you have on your laptop? 
If you suspect a BIOS problem, have you read up on [UEFI]("https://help.ubuntu.com/community/UEFI")?

---

### Post by oldfred on 2014-05-13
All Windows 8 pre-installed systems use UEFI with gpt partitioning.
Most reinstall Windows 7 with the DVD which only installs in BIOS mode. You have to convert DVD to flash drive and make a few updates to make a Windows 7 UEFI installer.
But the Windows in BIOS mode does not correctly convert gpt drive to MBR(msdos). It leaves the backup partition table.
You can either reinstall Windows 7 in UEFI mode, or use fixparts to remove backup gpt partition table and install Ubuntu in BIOS mode. You must be careful to always keep booting everything in which ever mode you choose, either always BIOS or always UEFI.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

      
 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---

