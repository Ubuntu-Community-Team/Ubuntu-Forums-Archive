---
title: "Can I actually install Ubuntu to a flash drive?"
date: 2014-08-15
forum: New to Ubuntu
---

### Post by dave131 on 2014-08-15
Just 2 weeks ago I got a new laptop - a cheap $300 but that was all I could possibly afford.  It seems to work fine.  Wouldn't you know - last night someone posted on our local Craigslist and I got a Dell Studio 1735 with a 17" screen, just no hard drive as they kept it.  I've booted it using the 64-bit regular Ubuntu live media and it runs fine - it seems it might be as fast, or possibly even faster, then the laptop I just bought new!  At any rate, while I wait for a used hard drive to show up (did I mention I can't afford much ;) ), I have a 32GB class 10 SD card, and I was wondering if I can actually install 14.04 to that media and use it until the drive shows up.  I'm particularly interested in getting the wifi working so I know how to do that when the disk arrives.  I apparently can't do everything I need to for that just running off the live media, not to mention it's not persistent storage.

Any guidelines for this would be greatly appreciated!

---

### Post by dave131 on 2014-08-15
I forgot to mention - the Dell laptop from Craigslist was FREE.  I could have saved almost $300!  Oh well, you never know what might come and go.

---

### Post by dave131 on 2014-08-15
Well, the installer showed the SD card and let me at try to install to it.  If it finishes ok I'll change my boot sequence and see what happens.

---

### Post by dave131 on 2014-08-15
Well, it apparently didn't work.  I don't know if the internal card reader isn't a device in the boot list or what, but it said no bootable disk found.

---

### Post by oldfred on 2014-08-15
Some newer systems do boot card drives. Just about all boot USB flash drives now.

But if new system, you have UEFI, UEFI with secure boot, and BIOS/CSM/Legacy boot modes. If you still have UEFI with secure boot on but created install in BIOS Mode it will not offer to boot it.
If you installed in UEFI mode, HPs will only boot a Windows efi entry and we have to create a work around just to even see it it might boot. The work arounds are required for hard drives or flash drives.

---

### Post by Sanctimonious_Ape on 2014-08-16
Would be surprised if a UEFI system was just given away - those are fairly recent and even the older ones are still worth something.

One thing that I'm wondering is how the card reader is attached to the system.  In 99% of cases even a built-in card reader is actually seen internally as a USB device.  You might want to check the BIOS settings to see if it's set to boot from USB.  It may matter what order the BIOS is told to look at devices in - make the USB boot first for the time being, but once you get a real hard disk switch it back to the way it is now.

Good Luck.

---

### Post by dave131 on 2014-08-16
It appears to be internally a USB device, but it's not booting.  I plugged in an external USB card reader and it booted ok now.  Having problems with wireless, but that's a different problem and I've created a seperate thread for it.

thanks everyone

---

