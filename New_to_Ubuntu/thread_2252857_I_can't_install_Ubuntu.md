---
title: "I can't install Ubuntu"
date: 2014-11-15
forum: New to Ubuntu
---

### Post by miles10 on 2014-11-15
I downloaded Ubuntu and used pendrive to put it an SD card (4 Gb) and a USB stick (2 Gb). I also burnt it onto a DVD
I previously tried to use Wubi to download Ubuntu. If I try to download the 12.04.5 version, everything seems fine until I reboot the computer, when it says that a file in C:/ubuntu is missing or corrupted. If I try to download the 14.04.1 version, the installation stops at the last second and says "Permission Denied"
Then I tried booting from a DVD, but it says "No Operating System Detected". Same for the SD card
I also tried booting from the USB stick, but it just gets stuck on my computers boot screen, although this is probably because the USB is an old, beat-up thing from 2008.

---

### Post by Impavidus on 2014-11-15
Wubi is no longer supported. It doesn't work on UEFI systems like most new computers. This includes all computers with preinstalled Windows 8. Wubi used to be a decent way of testing Ubuntu, but was never meant for prolonged use. Which version of Windows do you have?
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

Better have a look why you can't boot from the dvd, usb or sd card. Have you verified the image and burned in the correct way (as an image, not a file)?
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by miles10 on 2014-11-15
Ok, turns out you can't just drag and drop the .iso onto the disk. Don't get me wrong, I did burn it (which cost me a DVD). Thank you, you solved my problem.
Running Windows 8.1, in case you were curious.

---

