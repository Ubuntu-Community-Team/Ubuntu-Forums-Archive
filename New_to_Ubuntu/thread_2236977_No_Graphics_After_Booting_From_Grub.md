---
title: "No Graphics After Booting From Grub"
date: 2014-07-30
forum: New to Ubuntu
---

### Post by anarky2 on 2014-07-30
I installed Kubuntu 14.04 from USB today alongside Windows 7 in a dualboot, and while it installed fine. After I finished fooling around I rebooted, and after launching it from GRUB nothing appeared on screen, the screen remains lit, but blank, and nothing loads. Sometime a blinking cursor appears, but nothing loads. The same problem occured earlier with a debian install. Windows works fine. I have a AMD Radeon HD 7870 GPU.

---

### Post by zeebass1998 on 2014-07-30
I would suggest trying to reinstall Ubuntu in nomodeset.

---

### Post by yancek on 2014-07-30
> After I finished fooling around I rebooted,

Did this 'fooling around' happen on the Live/Install medium?  On the first reboot, do you see the grub menu?  You are able to boot windows but when you select Ubuntu you have the problem?

---

### Post by oldfred on 2014-07-30
I have nVidia, so I do not know AMD, but black screen is a video issue.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.

How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


 The AMD Radeon Performance Is Incredible On Linux 3.12
[http://www.phoronix.com/scan.php?page=article&item=amd_linux312_major&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_linux312_major&num=1)

   [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

### Post by anarky2 on 2014-07-30
Actually it is a issue with my DVD drive. I knew of this issue from debian, but didn't think it had affected my ubuntu. I thought it was due to it not accepting 16-byte commands from udev as said here [https://bbs.archlinux.org/viewtopic.php?pid=894147#p894147](https://bbs.archlinux.org/viewtopic.php?pid=894147#p894147), and so I thought the workaround to that was to add libata atapi_passthru16=0 to /etc/initramfs-tools/modules. I realized when live refused to boot as well that this was the cause of the problem, if the dvd drive is unplugged it works from the hard drive or live, however when attached neither do. It is a ASUS DRW-24B1ST attached to a ASRock Z77 Extreme4.

---

### Post by oldfred on 2014-07-30
A lot of users have reported issues with AsRock's asmedia ports. Not using them solves many issues.

 ubuntu 14.04 on asrock Z87 extreme 4 or pro 4 
[http://ubuntuforums.org/showthread.php?t=2216079](http://ubuntuforums.org/showthread.php?t=2216079)
Some have issues with Asrock and its asmedia ports
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)
AsRock Z77 Windows always reset to default
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order)

---

### Post by anarky2 on 2014-07-30
> **oldfred said:**
> A lot of users have reported issues with AsRock's asmedia ports. Not using them solves many issues.

 ubuntu 14.04 on asrock Z87 extreme 4 or pro 4 
[http://ubuntuforums.org/showthread.php?t=2216079](http://ubuntuforums.org/showthread.php?t=2216079)
Some have issues with Asrock and its asmedia ports
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)
AsRock Z77 Windows always reset to default
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order)

None of these seem to have the same problem, and I would prefer to keep using my CD/DVD drive as it would be a huge pain to open my computer every time I want to use it in windows.

---

### Post by oldfred on 2014-07-30
You should not have to change with Windows. Its just better not to use Asmedia ports, just the standard Intel based ones.

---

### Post by anarky2 on 2014-07-30
> **oldfred said:**
> You should not have to change with Windows. Its just better not to use Asmedia ports, just the standard Intel based ones.

Thanks this worked, I didn't even realize I was using a ASmedia port.

---

