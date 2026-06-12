---
title: "Can't USB boot from BIOs while on 12.04 + Grub."
date: 2012-10-03
forum: New to Ubuntu
---

### Post by Zaosyn on 2012-10-03
Hello, I recently did a full install of Ubuntu 12.04, replacing Windows 7, however now I am trying to go back to Windows 7 due to the lack of support for my current hardware on Ubuntu. I'm having issues with booting from USB as I have Windows 7 properly installed on a USB, however, when I change my BIOs to boot from USB first, it never does- instead, Ubuntu instantly boots up instead, befor the installation of Ubuntu my computer always booted into USB first- that's how I Was able to install the installation of Ubuntu.

I do not have a CD drive at this moment, only several USBs. I've tried to even create another LIVE Ubuntu USB so that I could use the LIVE version and remove the full installation of Ubuntu, however, again, my computer no longer boots into USB- instead it goes into Ubuntu.

Is there anyway to possibly boot from USB from GRUB? If so could someone please walk me through the steps as I never see the GRUB loader, my computer literally goes from the POST screen to Ubuntu, no special GRUB loader that allows me to pick if I want to go into Ubuntu or Ubuntu (Recovery Mode).

---

### Post by Bucky Ball on 2012-10-03
Hit shift after the BIOS screen. That will get you to the grub OS list. No ideas about how you would incorporate the USB in to that menu but guess anything's possible ...

---

### Post by dgharmon on 2012-10-03
> **Zaosyn said:**
> when I change my BIOs to boot from USB first, it never does- instead, Ubuntu instantly boots up instead

GRUB hasn't loaded yet so it's a problem with the USB device or BIOS settings.

---

### Post by Wim Sturkenboom on 2012-10-04
Have you tried the USB stick on another computer?

---

### Post by ppv on 2012-10-04
Do you know what is the key that takes you to BIOS setup menu. If yes, hit that key during startup.

Else, many of them have F9 to change boot device priority. So once you power up keep hitting F9 for a while and see if it takes you to a menu where you can change the boot device priority. 

Once you are into the menu, make your USB drive as the first boot device, save settings and let it boot.

Other keys to try would be F2 and F12.

---

### Post by AndyOpie150 on 2012-10-04
Something else that might help if you can't seem to get into the Bios. Try Plop Boot Manager.
I have an old 2003 SONY VAIO desktop that made it real hard to boot into a USB Drive. I installed Plop Boot Manager. On boot up I just selected from the options to select either Windows or it. Once inside Plop I scrolled down to the USB option.  The Ubuntu .iso  loaded right up (I used Penndrive Linux to get the .iso properly installed and configured to boot).

---

### Post by danisari on 2012-10-04
> **AndyOpie150 said:**
> Something else that might help if you can't seem to get into the Bios. Try Plop Boot Manager.
I have an old 2003 SONY VAIO desktop that made it real hard to boot into a USB Drive. I installed Plop Boot Manager. On boot up I just selected from the options to select either Windows or it. Once inside Plop I scrolled down to the USB option.  The Ubuntu .iso  loaded right up (I used Penndrive Linux to get the .iso properly installed and configured to boot).

I highly recommend this suggestion..

---

### Post by NikTh on 2012-10-04
Are you sure that Usb is bootable ?

---

### Post by Gregorybekkers on 2012-10-04
Try it on another computer. 
Is it doesn't work you can try to install it on your usb stick with Pendrivelinux (Windows) or format and install it with startupdisk creator.

---

