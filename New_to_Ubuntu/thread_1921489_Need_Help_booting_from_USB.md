---
title: "Need Help booting from USB"
date: 2012-02-06
forum: New to Ubuntu
---

### Post by DaimyoKirby on 2012-02-06
Hello.
I'm trying to turn on my computer, and boot into a USB - I have one with Memtest86+ on it, and another with a Xubuntu 11.10 installer on it, and I would like to be able to run those.
The problem is, whenever I press F12 to select what to boot from, USB isn't listed (as far as I can tell).

I'm running a Dell Dimension 2350 with Windows XP, and I'd really like to get back to Ubuntu...

Anyone know how to fix this?

---

### Post by DeezyFaReal on 2012-02-06
Hi, if usb isn't listed as one of the boot options, that can be changed in BIOS. To get to BIOS (Basic input output system), turn your computer on and immediately start pressing one of the F buttons. For example on my computer I have to press F10 to get to BIOS and then add USB Flash/Diskette to the boot options. On a Dell it might be F2.

---

### Post by mastergkage on 2012-02-06
Also if the flash drive is already been plug and cannot be detected in the bios try plugging it to a different usb port.

---

### Post by techvish81 on 2012-02-07
it's sometimes f2,f10, esc or del. press these buttons immediately at startup and enable external usb device boot option to make it visible in boot options.

---

### Post by varunendra on 2012-02-07
Some common issues with USB Flash-drive booting:

[LIST]
[*]Most BIOS have "Legacy USB" support option (or something similar). Try toggling it between enabled/disabled.
[*]Some BIOS have an additional option to enable/disable booting from USB. Make sure it is enabled, if your BIOS has that option. (almost what *DeezyFaReal*  suggested)
[*]Changing USB ports, as pointed out by *mastergkage* also works in some cases (reasons may vary from faulty to 'incompatible' port).
[*]Sometimes, even though the usb flash drive is detected, it gets listed under a different category (depending upon boot-menu structure + drive's 'emulation' mode), like hard-disks or floppy. Try expanding those categories if you have such menu.
[*]Sometimes, it takes the usb longer to get ready than the BIOS can wait for it. Two possible remedies are: **1)** try increasing the 'waiting time' in BIOS if there is such an option. **2)** 'Restart' the machine while the USB is plugged-in (that is, either let the installed OS detect it, then restart, or just 'Hot-reset' it while it is trying to boot).
[*]Even in some modern computers (like my HP Compaq DX2480), booting from USB flash drives is NOT SUPPORTED at all!! Yes, the "boot from usb" option is there in the BIOS, but it is meant for only USB HDDs/CD-Rom drives. This is a hopeless case :( (can use Plop though, but even that would require to boot from CD/LAN)
[/LIST]

---

### Post by chipbuster on 2012-02-07
> **varunendra said:**
> Some common issues with USB Flash-drive booting:

[LIST]
[*]Even in some modern computers (like my HP Compaq DX2480), booting from USB flash drives is NOT SUPPORTED at all!! Yes, the "boot from usb" option is there in the BIOS, but it is meant for only USB HDDs/CD-Rom drives. This is a hopeless case :( (can use Plop though, but even that would require to boot from CD/LAN)
[/LIST]


I have a mid-range motherboard from 2009 with a BIOS update for the hex core phenom II, and it can't boot from USB.

I also have a laptop from the same time running a BIOS from 2007 that supports booting into practically any USB device.

Sadly, it seems like bootability from USB is a bit of a luck of the draw. Check to make sure your computer can do it first (maybe check the manufacturer website?)

---

### Post by DaimyoKirby on 2012-02-07
Well, I checked the BIOS, and I had Legacy USB enabled, as well as the USB Controller.
When I pressed F12, the only choices listed were "Normal, Floppy, Hard-Disk Drive C:, IDE CD-ROM Device, LAN, System Setup, IDE Drive Diagnostics, and Boot to Utility Partition" - there doesn't seem to be any USB choice...

---

### Post by varunendra on 2012-02-07
> **DaimyoKirby said:**
> When I pressed F12, the only choices listed were "Normal, Floppy, Hard-Disk Drive C:, IDE CD-ROM Device, LAN, System Setup, IDE Drive Diagnostics, and Boot to Utility Partition" - there doesn't seem to be any USB choice...
Most of the laptop BIOS I have seen only list the USB when they detect a potentially bootable device on it. But yes, being an [old model]("http://www.pcworld.com/product/16545/dell_dimension_2350.html?p=specs"), it may not have that option at all. If it becomes sure that it completely lacks that option, you may try to upgrade its BIOS (if it's already not the latest one): [http://www.dell.com/support/drivers/us/en/19](http://www.dell.com/support/drivers/us/en/19)
**But updating BIOS is a bit risky operation, and it doesn't guarantee what you want**.

Also, it seems the desktop has a floppy drive. If it works, you can create a Plop bootable floppy which can then let you boot from USB, regardless of whether the BIOS supports it or not.

---

### Post by mastergkage on 2012-02-08
Sometimes it will not show usb, like in my case when i try to boot from my usb it shows Silicon power, for that is the brand of my flash drive, some cases usb hard drive Try to see if there is changes in the list if plug and unplugged your usb upon boot selection.

---

### Post by DaimyoKirby on 2012-02-13
Thanks to everyone for the suggestions!
I downloaded Plop, and I can now choose that on the boot list, and boot USBs through that; now I'm happily running Xubuntu 11.10 alongside Windows XP. :-D

Thanks so much!

---

