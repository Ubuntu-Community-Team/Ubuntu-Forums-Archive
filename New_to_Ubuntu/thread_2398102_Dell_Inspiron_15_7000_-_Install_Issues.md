---
title: "Dell Inspiron 15 7000 - Install Issues"
date: 2018-08-07
forum: New to Ubuntu
---

### Post by mmartinsthiago on 2018-08-07
Good morning!
I'm having a problem similar to that one, I've bought a Dell Inspiron 15 7000 Gaming (I guess) and I'm trying to install the Ubuntu 18.04. Everytime I've tried the instalation, it locks in the selection of the keyboard's type. In the beginning, there is a multiple choice: Install, Try the Ubuntu 18.04, <some that I don't remember> and Verify/Check for failures. I've tried with the three ISOs that I've downloaded, the first and the second it locks or in the selection of keyboard's type or in the desktop area; and the last one all three says that there are two corrupted files.

If anyone could help; I really want to try this distro, but in a dual boot.

Anyway, thanks!

---

### Post by oldfred on 2018-08-07
Moved to your own thread as Dell issues are not the same as Toshiba issues.

Dell works well with Ubuntu, but needs several settings in UEFI.
You need to change drives from RAID to AHCI. But if dual booting with Windows be sure to add AHCI driver to Windows first. Otherwise you have to change setting everytime you reboot.
Best to have UEFI Secure Boot off.
Also in UEFI turn off fast boot as that sometimes is so quick you do not have time to press any key to get into UEFI to make changes or UEFI boot menu.

In Windows turn off fast start up.

The 9 "easy" steps to install Ubuntu are in the link in my signature. Do not skip the backup step.

       DELL Inspiron 15 7000 18.04 needed boot parameters
[https://ubuntuforums.org/showthread.php?t=2386049](https://ubuntuforums.org/showthread.php?t=2386049)
[https://askubuntu.com/questions/1043842/running-ubuntu-via-live-usb-error-on-dell-xps-15-9560](https://askubuntu.com/questions/1043842/running-ubuntu-via-live-usb-error-on-dell-xps-15-9560)

---

