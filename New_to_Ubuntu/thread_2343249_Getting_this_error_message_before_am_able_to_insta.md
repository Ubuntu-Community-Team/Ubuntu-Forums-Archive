---
title: "Getting this error message before am able to install ubuntu desktop 16.04.1"
date: 2016-11-14
forum: New to Ubuntu
---

### Post by gapodaca on 2016-11-14
I am working with a new FRED (Forensics Recovery of Evidence Device) computer at my institution and am having issues installing Ubuntu/Bitcurator onto our second hard drive. The first "bay" has Windows 8 and 98DOS on it, and we're trying to install Ubuntu/Bitcurator onto the second "bay." 

I've followed the instructions provided here: [https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) ; and it seems to write the ISO image to the USB. However, I keep on getting this error message briefly before the Ubuntu loading screen pops up and kind of cycles through aimlessly until it starts the process all over again:

[    2.074246] xhci_hcd 0000:04:00.0: ERROR Transfer event for disabled endpoint
 or incorrect stream ring
[    2.074303] xhci_hcd 0000:04:00.0: @00000008694f7580 00000000 00000000 1b0000
00 01038001
[    2.079871] xhcd_hcd 0000:04:00.0: ERROR Transfer event for disabled endpoint
 or incorrect stream ring
[    2.079924] xhci_hcd 0000:04:00.0: @00000008694f7a40 00000000 00000000 1b0000
00 02038001
[    3.080201] sd 12:0:0:0: [sde] Asking for cache data failed
[    3.080244] sd 12:0:0:0: [sde] Assuming drive cache: write through
[    8.734985] usb 3-5: device descriptor read/64, error -110
[   13.951227] usb 3-5: device descriptor read/64, error -71
[   19.279631] usb 3-5: device descriptor read/64, error -110
[   24.495884] usb 3-5: device descriptor read/64, error -71

We don't have anyone to consult with at our institution, so I am left trying to figure out our problems on this user-friendly forum. Hopefully someone has some insight into our problem. 

For clarification purposes, the USB is connected to a 3.0 port located on the computer and is inserted before the machine is powered on. I press F8 during the boot process which allows me to select from a variety of drives. I am positive I 
selecting the correct drive because, as I mentioned, the Ubuntu loading screen pops up, but not before the error message displays. I've tried downloading the Ubuntu desktop version and the Bitcurator version separately, but keep on getting 
the same mistake. Perhaps someone has some insight??

Many thanks in advance.

---

### Post by col48 on 2016-11-15
This is beyond my understanding, but an internet search has thrown up this thread on this forum:

[https://ubuntuforums.org/showthread.php?t=1782546](https://ubuntuforums.org/showthread.php?t=1782546)

It all seems to involve blacklisting something called uas.
Posts 17 to about 21 may be the most useful.  I don't know how to approach applying this in your situation, since you won't yet have an installed Ubuntu.

I hope this is helpful.

PS: I used "Transfer event for disabled endpoint or incorrect stream ring" as my search term.  The issue has been seen across lots of distros.

---

