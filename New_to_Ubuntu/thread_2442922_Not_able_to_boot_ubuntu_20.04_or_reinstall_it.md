---
title: "Not able to boot ubuntu 20.04 or reinstall it"
date: 2020-05-09
forum: New to Ubuntu
---

### Post by gurbir2 on 2020-05-09
I am new to linux. I just baught Dell Vostro 15 3580 and I had windows 10 installed on it. I installed ubuntu 20.04 from usb. But now whenever I start my laptop , in first attempt the Dell logo doesn't disappear, and for next attempts Grub screen appears. When I select ubuntu, only a black screen appears(with NO blinking cursor in it). If I select from linux kernal option, the boot hangs at "loading ramdisk....." line (same happens for recovery mode). However, if i plug charger into my laptop before starting laptop, ubuntu loads without any problem.

Then I tried to install ubuntu 18.04. However, when I choose any option (like install , or try without install), then the screen goes off and laptop starts restarting again and again. Are there any solutions?

Note- the bios version is 1.4.1. and there is no PPT security option to be disabled in it.

---

### Post by ActionParsnip on 2020-05-09
Is this a dual boot system, please?

---

### Post by oldfred on 2020-05-09
Issues on Dell are common across many models, bigger difference if AMD or Intel CPU.
And is newer Dell you probably need newest version of Ubuntu.
Dell often needs newer drivers, and releases those. But they often take a bit before included in distributions.

For general UEFI install, see link in my signature.

If it booted with power connected, then it seems it may be a driver issue of some sort. Similar issue?
[https://www.dell.com/community/Precision-Mobile-Workstations/Precision-7540-will-only-boot-Linux-if-charger-is-connected/td-p/7449042](https://www.dell.com/community/Precision-Mobile-Workstations/Precision-7540-will-only-boot-Linux-if-charger-is-connected/td-p/7449042)

Dell  Inspiron 3670 UEFI update & AHCI worked
[https://ubuntuforums.org/showthread.php?t=2412152](https://ubuntuforums.org/showthread.php?t=2412152)
Dell Inspiron 3567 Review i3 7100u (Works well)
[https://ubuntuforums.org/showthread.php?t=2364642](https://ubuntuforums.org/showthread.php?t=2364642)
Dell Precision 3520 Turn off RAID & change to AHCI
[https://askubuntu.com/questions/1096492/installing-ubuntu-18-04-alongside-windows10-the-ssd-is-not-recognized](https://askubuntu.com/questions/1096492/installing-ubuntu-18-04-alongside-windows10-the-ssd-is-not-recognized)

Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)

---

### Post by gurbir2 on 2020-05-10
No. it has been solved. i just updated my bios version to 1.9.0. and it worked perfectly well.

---

