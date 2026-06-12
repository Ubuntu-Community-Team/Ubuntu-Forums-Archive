---
title: "USB Boot - No operating system found"
date: 2018-07-25
forum: New to Ubuntu
---

### Post by duncan9 on 2018-07-25
Hi All,

I have an Advent laptop that I am trying to install Ubuntu 18.04 on to. I have created a startup USB key from another laptop running 18.04 but continually get the 'No operating system found' message. I have tried it with other USBs an also isolating just the USB in the boot menu of the BIOS but to no avail.

Anybody have any other ideas as to what else to try?

---

### Post by Autodave on 2018-07-25
Have you put the installer on the USB as an .iso file?  What operating system is on the machine currently?

---

### Post by yancek on 2018-07-25
If you get that message when you try to boot the usb then the usb probably wasn't created properly.  What software did you use to create the bootable usb?

---

### Post by Taylz on 2018-07-26
Hi,

Just having migrated to Xubuntu myself I found it easier to download the .iso file and use "Startup Disk Creator", installed from the software centre, to make my USB stick a bootable live CD.

Regards,

Tayl.

---

### Post by dexterisawesome on 2018-07-28
what is the usb? 
(like the brand and the model number and stuff.)

---

### Post by duncan9 on 2018-07-30
It's a Kingston Traveler Data SE9 32Gb key. I'm trying to install it on to a Windows PC (although I'm quite happy to get rid of Windows on it). I used the Startup Disk Creator from my other Ubuntu laptop. I think the USB key is okay as when I insert it on other laptops it goes to the installer page. I've excluded all other options from the BIOS no the Advent (the Traveler Data key appears as a named Boot option) but am still getting the No operating system message. Any ideas?

---

### Post by oldfred on 2018-07-30
Is UEFI secure boot off?
Are you booting in UEFI boot mode or BIOS boot mode or is error before that.
If Secure boot on, it will not even show BIOS option.

Also many UEFI have settings for USB ports. You may have to allow full access or allow boot, particularly if UEFI Secure boot on, as USB boot is then not secure.

---

### Post by duncan9 on 2018-07-30
Many thanks for your replay Oldfred. I'm booting in BIOS 1.05AD. I don't think there is even an option for UEFI - it is a few years old.

---

### Post by oldfred on 2018-07-30
Is that the newest BIOS?
Is it old enough to be 32 bit?
What model?
How much RAM, you may need Lubuntu.

---

