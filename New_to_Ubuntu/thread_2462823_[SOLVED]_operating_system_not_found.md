---
title: "[SOLVED] operating system not found"
date: 2021-05-28
forum: New to Ubuntu
---

### Post by m-mrsk on 2021-05-28
Hello, I have Sony VAIO Z which I format and clean install Kubuntu. 
Live USB burning went all well and fine, installation was all well and good, no errors, but when I rebooted the PC, it shows operating system not found. 
I tried Boot-Repair, it does not work and I am very clueless to all this. I have reinstalled with many different options already. 
My PC is default UEIF, I have tried to install by using the entire disk and set up LVM or just using the entire disk. 
This is the boot repair summary: [https://paste.ubuntu.com/p/SsCQXKfzht/](https://paste.ubuntu.com/p/SsCQXKfzht/)

Could someone please help? T_T

---

### Post by tea for one on 2021-05-28
Is this the Sony VAIO Z with the 11th generation Intel processor?

If it is a Laptop/PC from 2021, you should perhaps try Kubuntu 21.04 with a newer kernel?

---

### Post by oldfred on 2021-05-28
Sony (and HP) are vendors that only want to boot "Windows" boot entry in UEFI.
Do not know if they have improved things as not seen many Sony systems lately. Make sure you have latest UEFI that is available for your system.

There are a couple of work arounds, depending on whether dual booting or just Ubuntu.
Dual boot systems will also boot a fallback/or hard drive entry at /EFI/Boot/Bootx64.efi. This is similar to the default entry for all external devices.
If only booting Ubuntu, the UEFI only checks description, not actual boot file. So we can create an Ubuntu boot entry using shimx64.efi or grubx64.efi but have "Windows" description.

This assumes ESP is sda1. But I am not seeing it as sda1, but inside LVM. UEFI cannot read LVM.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

See also:
man efibootmgr

---

### Post by m-mrsk on 2021-05-28
Hello, thank you so much for your reply. I have figured out the problem and have solved it. 
This is not dual booting, it is just Ubuntu. The UEFI is not configured to Windows booting, I think. 
It seems to be a problem of my hardware raid (0), GRUB cannot be installed correctly no matter what because it thinks the boot drive is not EFI. 
I had deleted the raid and it installed correctly. Although I do not know how to keep the raid array and install kubuntu successfully.

---

