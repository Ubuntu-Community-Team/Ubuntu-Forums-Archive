---
title: "X-server on a live ubuntu USB stick not working. Need help."
date: 2016-06-29
forum: New to Ubuntu
---

### Post by tequilamockingbird on 2016-06-29
Hello, I am David AKA Tequilamockingbird. I come to you with a perplexing problem. Okay, so, hacking, the art of exploitation. Get book, download the iso on the offical page. Burn it to a usb since this pc does not read and cd's. Rufus says its fine, reboot computer as normal, no problem. Booting up as normal, loading all the drivers n kernel crap. X-server is not working, do I want to examine the error or not. Yes, garbled text. No, computer does not respond. Hold down the power button untill the poor thing dies from choking and shuts down. I need help with this, since this book is REALLY good. I need a immediate fix.

---

### Post by Bashing-om on 2016-06-29
tequilamockingbird; Hi; Welcome to the forum.


What graphic's card(s) ?
Not Intel, try a boot parameter " nomodeset" :
Boot the liveUSB;
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> F6 key (other options) -> arrow down to the preset option(s) space or enter to accept and then the escape key to exit; 
Try "nomodeset" at this time; for other additions the boot options kernel boot line is now available, one may append "other" desired boot parameters to the end of the line that are not present in the "presets".
Enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.
Additional Drivers, location varies depending on the version, ->locate the Additional Drivers utility and install the recommended driver.

If this works in the live environment we can make it work in the install !

[INDENT][INDENT]all on the process
[/INDENT][/INDENT]

---

### Post by tequilamockingbird on 2016-06-29
Hi, hello, TequilaMockingbird here.
1. NVIDIA Geforce 210
2. How do I do this?
3. No splash screen, it just starts loading, and it all goes to "bad x-server dude, check it out"
4. See 3, no splash screen or install.
6. See 4 and 3.
7. How do I try nomodeset?

---

### Post by grahammechanical on 2016-06-29
I have the Nvidia GT220 which is based on the GT 210 and the open source video driver (Nouveau) works well with this video adapter. The Ubuntu install ISO image uses Nouveau.

I am guessing that the issue is with the monitor. When Linux loads it accesses a chip in the monitor to find the optimum screen resolution from the Extended Display Identification Data (EDID). If Linux cannot get that information then it cannot set the X Server (video server) to the right screen resolution. This is why we give the recommendation to use nomodeset.

This wiki page will show you how to get access to the Advanced Welcome page and its options. Work your way down to Changing the CDs Default Boot Options and look at section 6 - F6

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards

---

### Post by Bashing-om on 2016-06-29
tequilamockingbird; Well ..

If this system is EFI endowed;
In the install USB:
It is the escape key that grub looks for . As soon as the firmware screen clears in booting, spam the escape key  to get the language screen -> boot options screen .

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by tequilamockingbird on 2016-06-29
Hi, hello. It does nothing, spamming just makes it go to the bad x-server thinga majiger. Also, it says it cant load some cache-y thingies because of unsupported functions when it starts booting up

---

### Post by tequilamockingbird on 2016-06-29
Hi, this is a different scenario. This boots differently, and is not the latest version. Under the boot help menu, there are no options down there so that does not help much.

---

### Post by Bashing-om on 2016-06-29
tequilamockingbird; Welp;

I must question the copy of the .iso to the USB drive as an image .
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

we must know that the install medium is sound.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by tequilamockingbird on 2016-06-29
I can confirm a virtual box works. Runs fine. I guess I will just run it that way.
Also, FYI [not to sound rude but just fyi] I checked the md5 thing on my kali distro, can confirm it matched what it said on the page.

---

