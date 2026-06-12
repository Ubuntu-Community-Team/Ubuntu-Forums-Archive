---
title: "boot from an external usb hard drive"
date: 2014-06-27
forum: New to Ubuntu
---

### Post by openation1 on 2014-06-27
hello everyone......... I need help booting from my external hard drive............. I am running ubuntu on my external hard drive. Now that I am running windows on my internal hard drive I can get my external to boot up.............. please help me I would appreciate any help. Thank you......... I've tried to boot from bios F2 but it doesn't work.....

;)

---

### Post by papibe on 2014-06-27
Hi openation1.

Do you have grub installed on the internal hard drive?

Is it a BIOS or UEFI system?

The simplest way would be to check if, as most computers, there's a hot key during boot that allow you to get boot options.

In most computers is F2. If you pressing while booting you'll get to choose where to boot from.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by openation1 on 2014-06-27
I have a bios .............. but I tried to boot up from usb and it just doesn't work at all.......... on my external I have ubuntu 12.04 lts

---

### Post by papibe on 2014-06-27
A few ideas:

Get into the BIOS and set the USB as the primary booting device.

Google if you computer has a hot key while booting to select the device to boot from.

Regards.

P.S.1: another idea would be to install grub on the internal disk. When you upgrade grub, it will probe all disks to include all OSes on its menu.

P.S.2: installing grub would remove your Windows bootloader. Make sure you have created your recovery disks just in case.

P.S.3.: remember to backup your personal data in case you go the grub way.

---

### Post by Impavidus on 2014-06-27
If you install grub on the internal disk whilst keeping Ubuntu on the external disk, you won't be able to boot Windows with the external disk unplugged. You'd get a grub rescue prompt, which is not very nice.

---

### Post by oldfred on 2014-06-27
If you tell Boot-Repair that second drive is removeable it will install grub to external drive and install a Windows boot loader to the internal drive. 
Set BIOS to boot external drive first, and internal hard drive second. If external not plugged in, then it will boot from internal drive.

If for some reason that does not work post link it gives for BootInfo report.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

