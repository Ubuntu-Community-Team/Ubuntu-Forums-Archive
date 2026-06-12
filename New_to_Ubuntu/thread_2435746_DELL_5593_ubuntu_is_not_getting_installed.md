---
title: "DELL 5593 ubuntu is not getting installed"
date: 2020-01-25
forum: New to Ubuntu
---

### Post by rakesh1979 on 2020-01-25
my system is the new DELL 5593 .in the DELL WEBSITE  is said that the system in Ubuntu 18.04 LTS  supported 

LIVE CD itself is not booting...

I have disabled secure boot

I have disabled fast startup

i have upadted the BIOS

[COLOR=#0D0D0D][FONT=Roboto]i hav an SSD AND SATA HD ON A TENTH GEN DELL LAPTOP WHICH HAS WINDOWS 10 INSTALLED ON THE SSD. All are GPT. EVERY TIME I TRY TO INSTALL UBUNTU IT SHOWS several  ERRORS.  failed to start user manager for uid 121WINDOWS OS  IS INSTALLED ON SSD. THOUGH I MADE SOME FREE SPACE ON THE SSD, UNALLOCATED SPACE IS NOT SEEN WHILE INSTALLING UBUNTU.MOREOVER WINDOWS OS IS ALSO NOT DETECTED FOR ALONG SIDE INSTALLATION.     IT IS HAVING  OS(C) OF NEARLY 512GB,  DISK 1 PARTITITION 1 750MB, THREE HEALTHY OEM PARTITITIONS, ONE OF WHICH IS WINRETOOLS, OTHER IS DELL SUPPORT LAST ONE  ITB DRIVE HEALTHY PRIMARY PARTITION .SIR PLEASE HELP[/FONT][/COLOR]

---

### Post by guiverc on 2020-01-25
Did you verify the ISO after download to ensure it was perfect?  ([https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)) and then validate your write to install media using the "Check disc for defects" option ? ([https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck) where CD will refer to CD/DVD/hdd/ssd/thumb-drive or whatever media you wrote it to).

If the "*Check disc for defect*" option fails or won't run on your box (hardware), I usually walk it to another box, boot it there & attempt to check disc for defects on that box. If it fails on the second box, I just assume it's very bad & re-write my media.

Some other links that maybe helpful :-

[https://discourse.ubuntu.com/t/try-ubuntu-before-you-install-it/14014](https://discourse.ubuntu.com/t/try-ubuntu-before-you-install-it/14014)
[https://discourse.ubuntu.com/t/how-to-verify-your-ubuntu-download/14010](https://discourse.ubuntu.com/t/how-to-verify-your-ubuntu-download/14010)
[https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-windows/14020](https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-windows/14020)
[https://discourse.ubuntu.com/t/how-to-burn-a-dvd-on-windows/14008](https://discourse.ubuntu.com/t/how-to-burn-a-dvd-on-windows/14008)
[https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-macos/14016](https://discourse.ubuntu.com/t/create-a-bootable-usb-stick-on-macos/14016)
[https://discourse.ubuntu.com/t/how-to-burn-a-dvd-on-macos/14015](https://discourse.ubuntu.com/t/how-to-burn-a-dvd-on-macos/14015)
[https://discourse.ubuntu.com/t/how-to-burn-a-dvd-on-ubuntu/14022](https://discourse.ubuntu.com/t/how-to-burn-a-dvd-on-ubuntu/14022)

---

### Post by rakesh1979 on 2020-01-25
i had used a bootable pendrive  for creating LIVE CD and was checked in other laptops and was working fine


I just bought a new Dell 5593 with i5, 8GB, and 512GB NVmE and 1TB HD with preinstalled Windows Single Language, Yesterday  I tried to install Ubuntu 18.04 LTS without any luck. Installation is getting freezed at the first lines of the booting process of the installer.The isos created with rufus and balena, Etcher on windows and they worked as tested in other machine. The same errors occurred again

---

### Post by guiverc on 2020-01-25
> **rakesh1979 said:**
> i had used a bootable pendrive  for creating LIVE CD and was checked in other laptops and was working fine


Checked in other laptops? - does that mean you used the "Check disc for defects" option in the other laptops; if so then it's a valid test.

Otherwise unless the other laptops have identical hardware, thus used the same modules, you used the identical features/functions on the media, thus using same blocks/sectors AND you scanned logs for "squashfs" errors your other use is incomplete.

Though if you did verify it it using the "Try Ubuntu" option, doing the same functions to the 5593; then it does confirms it's not a hardware driver issue, as it worked fine on the other laptops which had to have identical hardware for your valid testing to be proof, leaving possible faulty hardware on the new dell 5593.

Did you use the "Check disc for defects" option on the other laptops?

---

### Post by oldfred on 2020-01-25
Dell typically needs UEFI update. And if SSD, firmware update for SSD. Even if new system.
Then you need to turn off fast boot in UEFI, and change RAID/Intel RST to AHCI.
Dell does have some unique drivers but they get added to either kernel or drivers, but can take a while to be included in a distribution.

May be better to use newer version of Ubuntu 19.10 or even 20.04 which will not be official until April and may have breakage. It will have an excessive amount of updates so you may want to reinstall after release just to houseclean all the cruft.

May be similar:
Dell Precision 5530
[https://ubuntuforums.org/showthread.php?t=2420905](https://ubuntuforums.org/showthread.php?t=2420905)
Dell 5230 with 3 m2 drives.
[https://ubuntuforums.org/showthread.php?t=2406057](https://ubuntuforums.org/showthread.php?t=2406057)

Dell 7791 UEFI update & some settings
[https://ubuntuforums.org/showthread.php?t=2431450&page=3](https://ubuntuforums.org/showthread.php?t=2431450&page=3)
Ubuntu 19.10 Provides Good Out-Of-The-Box Support For The Dell XPS 7390 Icelake Laptop
[https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1](https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1)
[https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options](https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options)
[https://wiki.ubuntu.com/Dell/XPS/XPS-13-7390-2-in-1](https://wiki.ubuntu.com/Dell/XPS/XPS-13-7390-2-in-1)
[https://ubuntuforums.org/showthread.php?t=2431791](https://ubuntuforums.org/showthread.php?t=2431791)

---

