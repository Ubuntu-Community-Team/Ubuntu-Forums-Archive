---
title: "Possible to tell if windows and/or ubuntu is installed in efi from boot-repair log?"
date: 2014-09-12
forum: New to Ubuntu
---

### Post by lewis5 on 2014-09-12
Here's the log: [http://paste.ubuntu.com/8327920/](http://paste.ubuntu.com/8327920/)

---

### Post by Dennis N on 2014-09-12
The partition table is MSDOS. (See lines 573, 581). So you can't be using UEFI for either one. Repair did not change that (786).

---

### Post by lewis5 on 2014-09-12
Okay thanks!
I'm having problems dual booting. I run boot-repair and it doesn't fix anything.
If I fix grub, on the grub menu, I only see Ubuntu. And then obviously if I fix MBR, I can boot only to Windows. 

The only weird thing I can think of is when I go into the boot menu, my cdrom drive is only EFI. 
My USB is has an option for EFI and legacy but using unetbootin, I can't boot from legacy. So I installed ubuntu using the EFI. Will that affect anything?

---

### Post by lewis5 on 2014-09-12
Oh and in my BIOS settings, boot mode is set to legacy and not EFI (I have the option to choose).

---

### Post by oldfred on 2014-09-12
If you install Ubuntu using UEFI, you may destroy Windows. 
Windows only boots from gpt drives with UEFI and only boots from MBR(msdos) with BIOS.
You cannot easily convert a BIOS install of Windows to UEFI boot.

You need to boot Ubuntu in BIOS mode to install in BIOS mode.

For whatever reason os-prober has not added a Windows entry to grub menu. Then you just default boot into Ubuntu.
Have you run this?
sudo update-grub

That should rerun os-prober and add Windows to grub menu. But if Windows needs chkdsk or is hibernated it cannot mount the NTFS partition, so cannot see that it contains boot files. Make sure Windows boots, and is not hibernated.

---

