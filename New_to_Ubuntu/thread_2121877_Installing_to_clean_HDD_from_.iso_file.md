---
title: "Installing to clean HDD from .iso file"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by Asolepius on 2013-03-03
Well I seem to be not even as expert as an absolute beginner! I tinkered with Ubuntu a few years ago and then got distracted. I had no problems installing it from a USB stick at that time. Now I want to start again, as I have a spare PC. It runs Phoenix Award BIOS. Because the HDD had some nasty errors I reformatted it in Windows 7 (before I decided to try Ubuntu again). This time though, I can't get even get it installed. The PC won't boot from the USB, although the BIOS has 3 options:

USB-HDD
USB-ZIP
USB-CD

Not sure what this means, and motherboard manual (Foxconn) is no help. So I have tried to burn a DVD, but it won't boot from that either (yes I did change the boot in BIOS). I am trying to follow the Ubuntu website instructions, which tell me to download the .iso file for Ubuntu. So far so good, but next the site tells me to right click (in Windows 7) and select the option to burn to DVD. I do not get this option in Windows. The DVD I have burned is not bootable - whatever I do the BIOS always says `bootmgr missing'.

Compared with my previous experience, installation has become vastly more complicated. Or have I misunderstood?

---

### Post by fantab on 2013-03-03
Ubuntu install is not complicated. If you are trying to burn the DVD from windows then you need **[Win32 Disk Imager]("http://sourceforge.net/projects/win32diskimager/"). **[COLOR=#000000][FONT=sans-serif]The Win32 Disk Imager's file browser assumes image files end with .img, so if the image-file you have selected ends with .iso, you will have to type its name in manually; this difference in suffixes is simply cosmetic however, the image will be written fine regardless. OR use [**UNETBOOTIN**]("http://sourceforge.net/projects/unetbootin/?source=directory").

Before you burn the downloaded Ubuntu.iso check the integrity of the download by running [**MD5Sum**]("https://help.ubuntu.com/community/HowToMD5SUM") Check.

In your case choose USB-HDD when you have to choose the boot device from BIOS.

Good Luck...[/FONT][/COLOR]

---

### Post by mJayk on 2013-03-03
Depends on the motherboard I believe USB-HDD is NOT what you want if you are booting from a usb stick believe it or not.  It will detect the usb stick as an actual HDD.  If it is a gigabyte motherboard (?) this problem is well known do a quick google gigabyte usb boot there are a few solutions depending on what you have at hand.

---

### Post by Cheesemill on 2013-03-03
On my Gigabyte mobo I *have* to choose the USB-HDD option. It's the only way I can boot from a USB stick.

---

### Post by oldfred on 2013-03-03
Actually on my Gigabyte motherboard it is under hard drives to find flash drive, not any of the USB options. So under f12 (one time boot key) I see my hard drives and if a bootable flash drive is plugged in before bootting, it shows the flash drive.

So is flash drive correctly installed with unetbootin or other installer and not just copied to flash drive?

---

### Post by darkcrimson on 2013-03-03
I've had issues with this in the past.

In the BIOS setup:
Change Hard Disk Priority to the USB drive. (it's set to the 2nd position by default, which is the reason you're unable to boot from it when selecting USB-HDD)
Change Boot Priority to USB HDD. (Which you can also select manually by holding down F12).

This will tell the computer that the HDD is actually your USB drive. As far as confirming whether or not Unetbootin properly installed the .iso to USB? You can always verify the contents or simply attempt to boot it from another machine.

Hope this helps.

---

### Post by Asolepius on 2013-03-03
Thanks guys. I'll need some time to work through all this. Busy week coming up - I'll check back here next weekend.

---

### Post by darkcrimson on 2013-03-03
It's no trouble at all. I hope you're able to get it working so you can enjoy the power of Ubuntu :D

---

### Post by debodas on 2013-03-03
If you have an ISO file, use Imgburn to burn the ISO to a dvd, then select the USB-CD boot option. It should work now.

---

### Post by Asolepius on 2013-03-12
I have now created the Ubuntu DVD, but the problem lies with the PC. It won't try to boot from the USB whatever I do, and although it tries to boot from the DVD, it reports that the disk is not bootable. This is not true, as the disk boots into Ubuntu on another PC. The boot priority in BIOS only gives me the HDD and `bootable add-in cards', whatever that means. All very baffling. The BIOS detects the CD/DVD drive,and displays it on the main screen, but doesn't add it to the options for selecting the priority. Something very odd with the BIOS firmware. Can it be flashed to correct this?

---

### Post by oldfred on 2013-03-12
Does not seem like a bootable DVD. Did you use imgburn? You cannot just copy ISO to DVD.

---

### Post by Asolepius on 2013-03-13
It is unquestionably a bootable DVD, because (as I said) it boots into Ubuntu perfectly on another PC. I did use imgburn, and before that checked the MD5 hash.

---

### Post by mastablasta on 2013-03-13
are you maybe using UEFI? Do you have secure boot?

---

### Post by zero-g on 2013-03-13
Hi Asolepius, I was going to say try flashing an updated BIOS or if you've got the latest flash it again incase there's a gremlin in there. Also you could try resetting the BIOS to defaults and see if that makes a difference. At least you can rule out the disc now.

---

### Post by Asolepius on 2013-03-13
OK, I have installed Ubuntu now. I had to swap the DVD drive as it was faulty. I still can't understand why neither USB nor the CD/DVD appears in the boot priority. So I never could install from the USB. But all's well that ends well.

---

### Post by Asolepius on 2013-03-13
Oops, forgetting my manners! Thanks guys for all your help. Just need to re-learn Ubuntu now!

---

