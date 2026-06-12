---
title: "Changed screen resolution now have black screen"
date: 2014-11-20
forum: New to Ubuntu
---

### Post by jdeblanc on 2014-11-20
I changed the screen resolution and my screen went black.  when I reboot, I get the login page.  After I log in, it goes black.  AGGGHhhhh  this is the first time I have ever used unbuntu / linux.  please help.

---

### Post by JeQhdMD on 2014-11-20
There is a way at bootup to make the system start using a generic (or vesa) video driver - normally set at 1024x768 on desktops.   To get that going, you have to edit the grub bootloader by:

[COLOR=#000000]"At grub menu you can use e for edit, scroll to linux line and replace quiet splash with [/COLOR][COLOR=#417394]nomodeset[/COLOR][COLOR=#000000]."

The nomodeset parameter should be typed as the last word on the linux line.

This should provide a very basic "safe mode" display, which then will allow you to run the setup program again and change the video resolution to what it should be.    If you're using a proprietary video driver such as for nVidia or ATI  . . . then you have to install those drivers (before changing the screen resolution).   This is done via Settings>Software & Updates>Additional Drivers tab (far right).   Once those drivers are installed, the resolution will be auto-set to the correct configuration.    IF you have an open source video such as Intel HD graphics, you don't need to do this additional drivers step.

BTW, if you want a reasonable chance to get answers on this board (or any other), you need to actually provide some basic info about your system (hardware specs) and what actual settings you originally had, and then what you changed it to (so you can avoid this kind of FUBAR in the future).[/COLOR]

---

### Post by bilkay on 2014-11-21
Have you tried cranking up the brightness setting?

---

