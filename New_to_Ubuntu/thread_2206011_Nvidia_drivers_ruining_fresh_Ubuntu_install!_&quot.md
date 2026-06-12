---
title: "Nvidia drivers ruining fresh Ubuntu install! &quot;nomodeset&quot; GTX 780 driver issues"
date: 2014-02-17
forum: New to Ubuntu
---

### Post by jared11 on 2014-02-17
Hi there! I have been trying to get Ubuntu to run on my PC for the better part of 5 hours now. I have Windows 7 and boot loader on my SSD and my swap/ubuntu partitions on a HDD.

PC SPECS:

4770k i7
AARock Z87 Extreme 6
EVGA GTX 780
120GB SSD
1TB HDD
8GB DDR3 RAM

I have tried both 13.10 and 12.04, they both have the same results/issues. The following is the issues as they appear in order:

**[SIZE=4]THE INSTALL[/SIZE]**

I launch via USB and there's an issue, it will not launch properly without "nomodeset". If I launch via USB without it, I get to the desktop wallpaper, bongo noise and all, but I can't see anything else. No mouse, UI, terminal, nothing. Just the desktop wallpaper. 

I restart and launch USB with "nomodeset" and I get to the desktop. I run the ubuntu installer, erasing the previous install (as I have done this multiple times today) and create everything that's needed. (swap, ubuntu partition, place the bootloader, etc.) 


**[SIZE=4]THE VIDEO DRIVERS[/SIZE]**

Once Ubuntu is installed, I launch and get to bootloader. I choose ubuntu and it launches fine. That said, by default, it is launching with "nomodeset". 

It launches fine and I can connect to the internet, make a backup, it pretty much runs smoothly. However, everything is very zoomed in and it's clear there's tearing when scrolling so it all screams a video driver issue. I have tried both the most recent linux nvidia driver from their site (to horrible results) and installing "nvidia-current" via terminal (to similarly horrible results). I have tried a number of things involving jockey-text and others. Whatever I could find on the web, tbh. :/  


[SIZE=4][B]THE RESULT

[/B][SIZE=2]When I relaunch with the freshly installed video drivers, the common result was that the following would flash on the screen:

[/SIZE][/SIZE][SIZE=3][I]*error* cannot initialize the agpgart module. drm fill_in_dev failed 

[SIZE=2][/SIZE][/I][SIZE=2]After this, depending on what settings I set and where, it would either take me to a screen that says I was in "low-quality graphics" mode, in which I could not see my mouse and the tab key only worked half the time or a full-screen black and white console in which I could login to and run commands. I have tried launching via recovery mode, using a number of useful sounding tools there, but nothing has helped. Whenever it gets to this point, Ubuntu is seemingly no longer accessible and I have to launch from USB, restarting the whole process to try again.
[/SIZE][I][SIZE=2]
[/SIZE][/I][SIZE=2]I understand that this has been quite the wall of text and I want to thank you if you made it this far. This has been driving me up the wall today and as a new ubuntu user, I don't want to be turned away so easily!
[/SIZE][I][SIZE=2]
[/SIZE][/I][SIZE=2]Any suggestions? I'm running out of hair to pull out.

Thanks in advance![/SIZE][I][SIZE=2]


[/SIZE]
[/I][SIZE=2][/SIZE][/SIZE]

---

