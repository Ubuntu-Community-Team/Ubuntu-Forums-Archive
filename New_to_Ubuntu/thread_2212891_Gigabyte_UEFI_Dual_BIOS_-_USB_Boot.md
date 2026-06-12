---
title: "Gigabyte UEFI Dual BIOS - USB Boot"
date: 2014-03-23
forum: New to Ubuntu
---

### Post by KAWill70 on 2014-03-23
I have a new Windows 7 computer with a Gigabyte UEFI Dual BIOS.  Windows 8 Mode Select in the BIOS specifies "Other OS".  With no USB bootable devices attached, the BIOS only shows the DVD drive and Windows Hard Disk as bootable devices.  No USB drive can be added.

If I plug in a Linux Flash Drive and reboot the BIOS, that specific drive will now show and can be added to the boot order.  Actually, two versions are available with the second one being a UEFI version of the Flash Drive.  I can then boot Linux on the Flash Drive.

Here is the problem.  Once I remove the Flash Drive, the USB entry in the boot order disappears.  It looks as though I would have to go into the BIOS each time I want to boot a different Linux USB device.  My older WinXP computer worked differently and I could insert any Linux Flash drive and it would be recognized and boot.

Does anyone know if the Gigabyte UEFI Dual BIOS can be configured to work differently and automatically boot any USB device?

---

### Post by oldfred on 2014-03-23
Does Windows 8 mode with your motherboard mean what everyone else calls UEFI secure boot?
With secure boot on, only systems that are configured for UEFI secure boot will be shown or boot. 
Then with secure boot off you may have both UEFI (without secure boot) and BIOS boot options.
Some require you to manually turn on/off UEFI or BIOS/CSM/Legacy modes, others auto switch based on what you tell it to boot.
But all systems must see a bootable device to offer it for booting. With my old Gigabyte BIOS system, it only shows a flash drive in the boot list if it is configured to boot. And if I set it as first in boot order it will boot until I remove it and then second choice in boot list is tried to boot. But when I plug it back in, it still is there.

Have you tried just setting it first in BIOS, then remove it and reboot, then plug it back in and reboot?

---

### Post by KAWill70 on 2014-03-23
The Windows 8 mode may indeed mean UEFI Secure Boot but I can't confirm at present.

I just tried what you suggested in terms of setting up the USB boot device in the BIOS, booting, removing it, booting Windows, and then inserting it again.  Yesterday that did not work with Mint 13, but today it did work with Mint 16.  The Flash drive was remembered and re-enabled in the BIOS boot order.

However, it was enabled in the UEFI version and not the generic version which I originally specified.  The UEFI version brought up a basically black & white Grub menu at boot where I could select Compatibility mode and other choices.  If I use the generic version it boots differently all in color.  I now need to repeat these experiments with Ubuntu.

This makes me wonder where any UEFI information or code comes from when booting with that choice.

Re: "But all systems must see a bootable device to offer it for booting."

That is not the case for my 9 year old WinXP computer.  I can set USB in the BIOS boot order and it will boot any Flash Drive that is inserted or otherwise go to the next device in the boot order.

---

### Post by oldfred on 2014-03-23
My 2006 vintage laptop will only show a USB device if bootable. And if I have two USB devices plugged in it does not know which to use and does not work.
With my 2009 Gigabyte (BIOS only) motherboard, it took me forever to find how to boot a flash drive. It had many USB boot options and none worked. One day in changing which hard drive to boot from, I had flash drive in USB port and it worked. So a USB flash drive with my motherboard is seen as another hard drive not as a USB device. So it is hard drive boot order I have to set, not DVD/USB/hard drive choice which is separate.

---

### Post by KAWill70 on 2014-03-23
Thanks for the note on setting hard drive boot order as a separate choice from the DVD/USB/HD choice.  Interesting that the USB device is seen as another hard drive even if a thumb drive.

The BIOS in my WinXP computer is definitely different.  I just checked the menu and there are a total of 11 devices that may be selected for boot.  That includes Floppy, LS120, Hard Disk, CD Rom, Zip, USB-FDD, USB-Zip, USB-CDROM, USB-HDD, LAN, and Disabled.

As I recall all those choices are available for all three selections in the boot order.

I use USB-HDD for my Linux Flash Drives.

---

### Post by KAWill70 on 2014-03-24
Here is an update to this thread.  I have now inserted two different Linux Flash drives and the Gigabyte UEFI Dual BIOS remembers each one.  If either one is reinserted later, it is recognized by the BIOS.  One is listed as HP 2G (currently with Mint 16) and the other as Cruzer (currently with Linux Lite).

In both cases, the USB Flash Drive is again placed at the top of the boot order but in the UEFI version and not the generic version.  It now gets more interesting.  The HP 2G with Mint 16 boots just fine in the UEFI version.  The Cruzer with Linux Lite does not boot and Windows boots instead.

Could it be that Mint 16 is signed properly under UEFI while Linux Lite is not?  To boot Linux Lite it looks like I will have to manually intervene in the BIOS and enable the generic version instead of the UEFI version for that Flash drive.

---

### Post by oldfred on 2014-03-24
Very likely.

With secure boot on, only those systems that are secure boot will be offered to boot.
Or it could be a BIOS only version and you have to change from Secure boot to CSM/Legacy/BIOS boot mode.
Some auto switch between standard UEFI and BIOS, but not secure boot.

---

