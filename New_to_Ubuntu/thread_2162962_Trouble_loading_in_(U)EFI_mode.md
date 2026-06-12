---
title: "Trouble loading in (U)EFI mode"
date: 2013-07-16
forum: New to Ubuntu
---

### Post by ZRos on 2013-07-16
I am very new to linux so I'm not sure I even need to do this, but, 
When I boot my computer and go to the boot menu it says that I can load ubuntu in EFI mode.  When I click on it grub2 starts up and to start ubuntu I just type exit.  But It loads in legacy mode instead of EFI mode.  If I try and boot it from grub2 it says you must load a kernel first.  I don't know how to load a kernel or if it is even necceccary but I would appreciate any help.  I am using a computer which came with a x64 windows 7 OS with EFI.

---

### Post by CinTUX on 2013-07-16
Do you want to install Ubuntu besides another operating system or just a full install?

---

### Post by oldfred on 2013-07-16
What computer and what version of Ubuntu? You do need the 64 bit version of Ubuntu to install in UEFI mode.

If Windows is installed in UEFI mode, you should install Ubuntu in UEFI mode. Or both should be installed in BIOS/CSM/Legacy mode.

A lot of info on UEFI boot with Link in my signature. If Windows 7 you will not have any of the secure boot issues as that is only systems with Windows 8 pre-installed.

---

### Post by ZRos on 2013-07-16
It is windows 7 64 bit and I downloaded the 64 bit version of ubuntu 13.04.  Windows is in UEFI mode and the option to launch ubuntu in UEFI mode comes up but when I press it the grub2 command line comes up and when I type the command exit it boots ubuntu in Legacy mode.  And I want to install it along with windows.

---

### Post by oldfred on 2013-07-16
How you boot is how it installs, but if booting flash drive installer from grub you should be in UEFI mode. What setting do you have in UEFI/BIOS. You should have UEFI on, secure boot off if possible and legacy/BIOS/CSM off.

But even if it installs in BIOS mode, you can use Boot-Repair to convert a BIOS install to UEFI by uninstalling grub-pc and installing grub-efi. If system only boots with secure boot then you have to boot live installer in secure boot mode and use Boot-Repair to add the signed kernel and version of grub.

---

