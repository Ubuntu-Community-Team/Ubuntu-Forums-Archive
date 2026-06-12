---
title: "Dual Boot for Linux with Windows 10 on Dell XPS 13 not working"
date: 2018-06-24
forum: New to Ubuntu
---

### Post by goldenyogurt on 2018-06-24
[LEFT][COLOR=#222222][FONT=Verdana]Hi, I am new to this whole Ubuntu dual boot process. I have a Dell XPS 13 9350 i5-6200U 8GB RAM 256GB SSD and Intel Integrated Graphics 520. I have come across a problem where during the Ubuntu installation process, the Ubuntu does not recognize my PCIe M2 SSD. I have followed every single step on the Dell website for dual booting Ubuntu with Windows 10 such as shrinking the volume of my OS partition, making an 80 GB partition , downloading Ubuntu 18.04 through Canonical on my 128 GB SanDisk flashdrive, running it through Rufus, restarting the computer, hitting F12 rapidly until directed to boot menu, booting into SanDisk loaded with Ubuntu, hitting install Ubuntu without trying it out, and starting the installation process. Whenever I get to the installation type where I select my partition , nothing shows up. No partition, nothing. I went on the GParted app on the tryout mode and it can only recognize the flashdrive but the SSD is no where to be seen. Does anyone have a solution to fix this problem? I even tried loading 16.04 just to see and the same exact screen shows up. I am going to attach photos of the process for reference. Thanks![ATTACH=CONFIG]280207[/ATTACH][ATTACH=CONFIG]280208[/ATTACH][ATTACH=CONFIG]280209[/ATTACH][ATTACH=CONFIG]280210[/ATTACH][ATTACH=CONFIG]280211[/ATTACH][/FONT][/COLOR][/LEFT]

---

### Post by yancek on 2018-06-24
Almost certainly, you failed to turn off hibernation/fast boot in windows before beginning the process.  There are hundreds of threads here from people with this exact problem.  Reboot windows and turn off fastboot and anything related to hibernation.  I would also suggest that before you try installing Ubuntu again, you read the Ubuntu documentation on dual booting with windows 10 at the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by goldenyogurt on 2018-06-24
hi yancek, I have turned off fast start up in the power options in the control panel. Hibernation has been turned off as well.

---

### Post by oldfred on 2018-06-24
+1 on Yancek's suggestions.

Almost all Dell need UEFI update and SSD firmware update.
Issues with Dell are common across many similar models.

Also most new Dell systems have drives set for RAID, even if just one drive.
You need to install AHCI drivers in Windows and change UEFI settings to AHCI.

       XPS 13 9350 Windows reinstall & discussion of RAID vs. AHCI
[https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/](https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/) 
            [https://askubuntu.com/questions/696413/ubuntu-installer-cant-find-any-disk-on-dell-xps-13-9350/743329#743329](https://askubuntu.com/questions/696413/ubuntu-installer-cant-find-any-disk-on-dell-xps-13-9350/743329#743329) 
            Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488) 
            Ubuntu 16 on the DELL XPS15 9550 Tutorial
[https://ubuntuforums.org/showthread.php?t=2345444](https://ubuntuforums.org/showthread.php?t=2345444)
Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch) mega-thread
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)

---

### Post by goldenyogurt on 2018-06-25
Thanks Guys, I did some research and found out that for the Dell XPS, you have to change the SATA config from RAID to AHCI on the BIOS setup

---

