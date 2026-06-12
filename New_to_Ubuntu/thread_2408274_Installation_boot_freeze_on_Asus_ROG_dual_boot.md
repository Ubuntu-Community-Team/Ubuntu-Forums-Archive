---
title: "Installation boot freeze on Asus ROG dual boot"
date: 2018-12-16
forum: New to Ubuntu
---

### Post by tomnomdom on 2018-12-16
Trying to install Ubuntu 18.04.1 on my Asus ROG desktop in dual boot with windows 10. 

After selecting Try Ubuntu or Install from grub, the screen freezes several seconds into booting (see screenshot - taken with nomodeset param). [ATTACH=CONFIG]281949[/ATTACH]

Steps I've taken:
- Used rufus to create bootable usb
- Disabled fast startup in win 10
- Updated bios to version from 14/9/18
- Disabled secureboot and fastboot in bios
- Tried using nomodeset, acpi=off, nouveau.modeset=0 tpm_tis.interrupts=0 acpi_osi=Linux i915.preliminary_hw_support=1 idle=nomwait in different combinations. None helps, but sometimes the screen hangs up on different messages.

Motherboard:ROG STRIX B360-G GAMING
This PC: [https://www.alza.cz/alzapc/alza-gamebox-gtx1080-d5293818.htm](https://www.alza.cz/alzapc/alza-gamebox-gtx1080-d5293818.htm)

Could someone please help me?

Thanks.

---

### Post by oldfred on 2018-12-18
This may be so new you need newer kernel.

       Asus B350M-A needs newer kernel that 18.04 default
[https://ubuntuforums.org/showthread.php?t=2391892](https://ubuntuforums.org/showthread.php?t=2391892)
[https://ubuntuforums.org/showthread.php?t=2390660&p=13799816#post13799816](https://ubuntuforums.org/showthread.php?t=2390660&p=13799816#post13799816)
MSI Tomahawk B350 with Ryzen R5 1600 New UEFI required
[https://ubuntuforums.org/showthread.php?t=2390475](https://ubuntuforums.org/showthread.php?t=2390475)
ASUS PRIME B350M-E major issues
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux)
ryzen acpi=off only 1 cpu, needs nomodeset & then nVidia driver instead
[https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu](https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu) 
    
When I built my system in 2016, I used 16.04 several months before it was released. It did not have any major hiccups, but any install of a system that is still in development should not be your main working install.
You might try 19.04, I have it installed in my 2016 build and it currently works ok.But I still have 18.04 as main working install.
19.04 does already have newer kernel.

---

