---
title: "Grub installation failed"
date: 2019-01-30
forum: New to Ubuntu
---

### Post by vladimir.risojevic on 2019-01-30
I installed Ubuntu 18.04 over the previous Fedora install on a system that also has Windows 10 installed. However, it won't boot. I tried to repair Grub following the instructions from [https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd), but after I performed ```
sudo grub-install /dev/sda
``` it returned the grub-install: error: cannot find EFI directory.
The Boot-Repair report is [http://paste.ubuntu.com/p/XWySGsRrKF/ ]("http://paste.ubuntu.com/p/XWySGsRrKF/")

Any suggestions?

---

### Post by oldfred on 2019-01-30
Vendors are required to install Windows 10 in UEFI boot mode to gpt partitioned drives.
Although your hardware is UEFI, your Windows installs are BIOS on MBR(msdos) partitioned drives.
So you cannot install the Ubuntu UEFI version of grub to an ESP - efi system partition as you do not have one.
You just need to boot in BIOS mode and install the BIOS boot version of grub.

Also grub does not use boot flag, move boot flag on sda, back to NTFS partition with Windows boot files.
Also best to only have grub in the MBR of one drive with Windows 10, as it will keep turning on its fast start up or need chkdsk and then grub will not boot it. But if Windows drive in NVMe drive has Windows boot loader, you may be able to directly boot the NVMe drive and fix Windows. But still best to always have a Windows repair flash drive or installer with repair console.

---

### Post by vladimir.risojevic on 2019-02-01
Thanks for the help. I booted the installation USB in BIOS mode and installed Ubuntu from the scratch. It works now!

Thanks, again!

---

