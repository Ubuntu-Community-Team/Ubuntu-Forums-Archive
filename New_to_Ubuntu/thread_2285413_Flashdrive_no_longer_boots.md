---
title: "Flashdrive no longer boots"
date: 2015-07-05
forum: New to Ubuntu
---

### Post by numeric2 on 2015-07-05
Hi,
My Ubuntu flashdrive no longer boots, although there is nothing wrong with the flashdrive. My computer lost GRUB 2 UEFI configuration. I was messing around with "easy BCD" and deleted a duplicate "Windows boot manager" boot option. Something got screwed up, now the flashdrive no longer boots. 
When it did boot successfully, the first screen was a grub 2 bash screen. I had to type [COLOR=#ff0000]**exit**[/COLOR] to get to the grub2 boot list. Selecting boot option 1 or 2 booted to Ubuntu. 


1. Is there a way to restore the PC's GRUB2 configuration without loosing the data on the Ubuntu 14.02.2 LTE flashdrive? It may be file like windows/system32/winload.efi that needs to be changed. 
a. I know that I can re-load Ubuntu from scratch; but would really like to avoid a Ubuntu re-install.
    b. The "Try and decide" flash drive still works boots to Ubuntu. The  ISO file was downloaded from the Ubuntu web site and "burned" to a USB  flash drive with Rufus.
2. Can the need to type **[COLOR=#ff0000]exit[/COLOR]** be eliminated?
    

Using Windows 8.1 64 bit
Dell Inspiron 13 7000 series
Intel i7 5th generation CPU.
Sandisk Extreme USB 3 64 GB flash drive for Ubuntu 14.04.02 LTE
UEFI, Secure boot mode.

Thank you

---

### Post by sandyd on 2015-07-05
> **numeric2 said:**
> Hi,
My Ubuntu flashdrive no longer boots, although there is nothing wrong with the flashdrive. My computer lost GRUB 2 UEFI configuration. I was messing around with "easy BCD" and deleted a duplicate "Windows boot manager" boot option. Something got screwed up, now the flashdrive no longer boots. 
When it did boot successfully, the first screen was a grub 2 bash screen. I had to type [COLOR=#ff0000]**exit**[/COLOR] to get to the grub2 boot list. Selecting boot option 1 or 2 booted to Ubuntu. 


1. Is there a way to restore the PC's GRUB2 configuration without loosing the data on the Ubuntu 14.02.2 LTE flashdrive? It may be file like windows/system32/winload.efi that needs to be changed. 
a. I know that I can re-load Ubuntu from scratch; but would really like to avoid a Ubuntu re-install.
    b. The "Try and decide" flash drive still works boots to Ubuntu. The  ISO file was downloaded from the Ubuntu web site and "burned" to a USB  flash drive with Rufus.
2. Can the need to type **[COLOR=#ff0000]exit[/COLOR]** be eliminated?
    

Using Windows 8.1 64 bit
Dell Inspiron 13 7000 series
Intel i7 5th generation CPU.
Sandisk Extreme USB 3 64 GB flash drive for Ubuntu 14.04.02 LTE
UEFI, Secure boot mode.

Thank you

Try using a Windows 8.1 recovery media (USB/CD) to boot up the system, and try using Startup Repair.

The Ubuntu 14.04 USB drive could be possibly missing the boot loader. That can be recovered by using another USB drive with the Ubuntu ISO flashed to it. Run boot-repair on the USB drive with the Ubuntu ISO, and boot-repair should make the USB drive bootable again.

---

