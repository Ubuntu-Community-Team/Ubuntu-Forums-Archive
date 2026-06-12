---
title: "Dual boot Windows 10 and ubuntu 18.04 problem"
date: 2018-11-24
forum: New to Ubuntu
---

### Post by spookywooky5 on 2018-11-24
I had a dual booted Windows 10 and Ubuntu 18.04 machine.

Last month I decided to uninstall and reinstall ubuntu due to some reasons. I deleted the disk ubuntu partition entirely and I also deleted grub. But somehow when I restarted my computer I was still seeing the grub console. To get out of that I had to type in exit three times to boot into Windows. I followed a guide and tried installing Ubuntu using Unetbootin but I couldn't. On top of that now I couldn't even boot into Windows. Instead, I got an error which said I corrupted the hard drive. Then I installed Windows 8(with a cd) on my machine to access Windows 10. So now I have Windows 8 and Windows 10 on my machine. During boot, I get the windows bootloader screen with 3 options --> Windows 10, Windows 8, Unetbootin.

Now I want too install Ubuntu 18.04 the right way and uninstall Windows 8 from my pc and keep Windows 10 and Ubuntu 18 in dual-boot. Please help me. I am a complete newbie to Ubuntu and Linux.
Thank you very much.

---

### Post by oldfred on 2018-11-24
First lets see where you are.
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 
    
You do have to get live installer working.

If UEFI, you have UEFI boot entries in UEFI and grub & Windows initial boot files in the ESP - efi system partition. To change boot, you just select new default in UEFI or use efibootmgr in Ubuntu or live installer to change boot order.
See this:
man efibootmgr

       Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Ubuntu install guide - multiple ways to create live installer to flash drive
[URL="https://help.ubuntu.com/community/Installation"]https://help.ubuntu.com/community/Installation

      [/URL]
 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formatted flash drive partition & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb) 
    [URL="https://help.ubuntu.com/community/Installation"]
[/URL]

---

