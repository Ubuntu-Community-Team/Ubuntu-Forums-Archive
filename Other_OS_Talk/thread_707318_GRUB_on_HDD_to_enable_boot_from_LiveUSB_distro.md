---
title: "GRUB on HDD to enable boot from LiveUSB distro?"
date: 2008-02-25
forum: Other OS Talk
---

### Post by r76 on 2008-02-25
My laptop doesn't have an option to boot from USB in the BIOS (Acer TravelMate 372).  So my current pendrivelinux USB stick isn't bootable. However I was wondering if it's possible to install GRUB or something similar on the hard drive, offering dual boot option between Windows XP (on hard drive) or a USB stick (which may or may not be present) with a persistent live install of a linux distro on it?

If anyone knows a method by which I'd be able to boot with various liveUSB distros without having to reconfigure GRUB, it'd be much appreciated.

EDIT: NEVER MIND - I found a solution (for my BIOS anyway), the clue was in [these screenshots]("http://www.pendrivelinux.com/2006/08/29/setting-usb-boot-options-phoenix-award-bios/"), I have a version of the Phoenix Bios too. First had to set "USB legacy" enabled on another page of the BIOS, and then reboot and enter setup again - now the USB stick is listed under the list of hard drives (NOT as I expected as a removable device) - and can then be moved up in the order, above the internal HDD.

---

