---
title: "Nomodeset and Boot Repair"
date: 2014-06-20
forum: New to Ubuntu
---

### Post by Jack_Ryan on 2014-06-20
Hello all!
Yesterday I booted up my first ever Linux OS and man am I pumped! I have already done a ton of research on the terminal and its commands, but I have two quick questions that I hope can be answered with relative ease...

_The first:_ When I first was having big problems with booting from my USB, someone told me to type "nomodeset" in place of "quiet splash" in the Linux line at bootup. Although this worked perfectly and allowed me to start using Linux, I still have no idea why that worked or what "nomodeset" even means. Also, do I have to continue typing it in every time I boot up? I have been, just to be safe. 

_The second: _In the guide I was reading, I was presented with a few command lines which I believe were intended to install a Boot Repair to fix some of the "most frequent" booting issues. However, when I went to the terminal to find it, I was told that it doesn't exist or something along those lines. Does anyone know if I messed up here or, if it does not exist, is there an alternative solution?

Thanks in advance for all your help, this community is so great about quick and informative responses.

P.S. I run on a Lenovo IdeaPad Y500, the Linux distro is Ubuntu, my other OS is Windows 8, I already went through the partitioning/shrinking/etc and it all works great from what I can tell. I'll be checking this thread frequently throughout the day so if you need any additional information feel free to ask.

---

### Post by grahammechanical on 2014-06-20
nomodeset

In the old days when we installed an operating system we had to tell the installer about the monitor - its horizontal and vertical refresh rates, its resolution and video modes. An example from my old CRT monitor handbook looks like this 

> VGA mode, horizontal frequency at 31.5 Khz non-interlace
640 x 350 pixels (EGA emulation) / 70 Hz
640 x 400 pixels (VGA) / 70 Hz
640 x 480 pixels (VGA) / 60 hz

Just do not ask what all that means. :)

Today we do not need to give the installer any information about the monitor because modern monitors store the information in their electronics. It is called Extended Display Identification Data (EDID). The OS reads the EDID every time it loads and sets the optimum screen resolution as decided by the manufacturer.

When we use nomodeset (no mode set) we load the OS without it checking the EDID and without it setting a video mode and sometimes with certain hardware we need to do that to get the live session to load and an install to take place.

Once we are at the desktop we can use System Settings>Software and Updates>Additional Drivers tab to experiment with video drivers and that might fix the problem.

As regards the second question; it all depends upon the instructions you were following. Linux is case sensitive and will give a "command not found" message if we mis-spell the command. Then again, what you were typing might not have actually been a command.

Boot repair utilities fix certain boot problems but they are not a magic pill that fixes every boot problem.

Regards.

---

### Post by oldfred on 2014-06-20
If you installed Boot-Repair in your live installer and do not have it configured for persistence it does not save anything. It is just like a DVD and loads everything in RAM, but once shutdown it all is gone. You can add persisitence to a live flash drive to save some info, but still cannot update system.

If you have dual video you need to review latest info. It used to be that you had to install bumblebee as nVidia driver did not work with dual video. But nVidia has updated it to at least partially work. So you may not want bumblebee now.

       Testing NVIDIA Optimus / DRI PRIME On Ubuntu 14.04
[http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_prime_ubuntu1404&num=1)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

You can go to sysem settings and install the most current nVidia from Ubuntu repositories. That is very current, but not the newest from nVidia as it releases beta, then releases it and Ubuntu tests it before adding to repository. Best to use Ubuntu version unless you have a very new nVidia card/chip. And do not just install a second nVidia driver. You invariable get conflicts which make it worse. You have to totally purge old on boot with nomodeset again and install different driver.

---

