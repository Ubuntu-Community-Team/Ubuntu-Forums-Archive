---
title: "grub does not detect usb"
date: 2019-06-13
forum: New to Ubuntu
---

### Post by acanesse on 2019-06-13
Hi all,

I am trying to install Windows 10 from a usb stick on  ubuntu 18.04 with grub 2.02. My laptop initially came without OS and ubuntu is the only  OS I ever had on it. I would like now to have a dual boot system with  both windows and ubuntu.

So I created a Windows bootable usb as explained here: [https://itsfoss.com/bootable-windows-usb-linux/](https://itsfoss.com/bootable-windows-usb-linux/)
But when I try to boot on it, the option does not appear in grub and I cannot see the usb device. I tried to find answers online but I am still stuck.
 I tried to use boot-repair  ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) and it did output a lot of info on my system that  might be useful: [http://paste.ubuntu.com/p/F2w7zvCrrP/](http://paste.ubuntu.com/p/F2w7zvCrrP/)
But it I still can't see the usb as an option in the grub menu.

Thanks to boot repair though I can now see my usb via the command line (which is already a small improvement) with:
```
root (hd <tab completion>
```

and tried to use
```
set root=(hd0)
chainloader +1
boot
```
but at the second line I then get the message: "error: invalid EFI file path."

Am I on the right track and does someone know what commands you I use to boot on my usb?
Or does anyone have another method to make the usb appear on my grub menu so I can boot on it?

Thanks a lot!

---

### Post by aysiu on 2019-06-13
That bootable USB is for installing Windows. It isn't Windows. It's the Windows installer. I don't think you're going to have a good time of trying to install Windows as a dual-boot with Ubuntu **after** Ubuntu is already installed. This method used to work, which involves using a live USB to resize the Ubuntu partition (and make room for the Windows one), but then you have to fix Grub afterwards: [https://unix.stackexchange.com/a/286317](https://unix.stackexchange.com/a/286317)

---

### Post by oldfred on 2019-06-13
You have an UEFI system.
And you have Ubuntu installed in UEFI mode on sdb.

But your sda is MBR with a very large FAT32 partition.
FAT32 is only recommended for smaller partitions or devices. It cannot support files over 4GB and has no journal so recovery from errors is difficult or maybe impossible.

You have to directly boot an installer from UEFI boot menu.
Windows only installs in UEFI boot mode to gpt partitioned drives. 
And Windows only installs in the now 35 year old BIOS boot mode to MBR partitioned drives.
Installer flash drive may be MBR or gpt, but some systems only like one or the other. Installer must be FAT32 formatted.
How you boot install media UEFI or BIOS, is then how it installs.

With Windows may be best to disconnect Ubuntu drive or turn it off in UEFI settings so not seen.
And convert sda to gpt before installing. If you want to keep FAT32 partition shrink it before installing. If you add boot flag (make active in Windows), it will be used as the ESP - efi system partition.

       UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
[https://help.ubuntu.com/community/mkusb/v7#Making_a_USB_drive_to_install_Windows](https://help.ubuntu.com/community/mkusb/v7#Making_a_USB_drive_to_install_Windows)
C.S. Cameron and Sudodus with screen shots
[https://askubuntu.com/questions/962536/partitioning-a-usb-and-making-separate-bootable-drives](https://askubuntu.com/questions/962536/partitioning-a-usb-and-making-separate-bootable-drives)

---

