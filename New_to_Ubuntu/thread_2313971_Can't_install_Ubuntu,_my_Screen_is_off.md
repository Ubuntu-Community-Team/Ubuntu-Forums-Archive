---
title: "Can't install Ubuntu, my Screen is off"
date: 2016-02-17
forum: New to Ubuntu
---

### Post by les11 on 2016-02-17
Trying to install Ubuntu 14.04.3 LTS, as soon as the computer starts to load the disk my screen goes off and stays off.

So i can't see anything.

System..

Gigabyte Gaming 3 Z97
Intel Core i5 4690K
Gigabyte Windforce GTX 970
Kingston Hyper-X Savage 2400 (2x 8GB)
EVGA Supernova GS 650

Screen: LG IPS 226V

---

### Post by buzzingrobot on 2016-02-17
Most likely it's the Nvidia video card, which is a recent model. 

The Linux kernel detects hardware components when it boots and then loads the appropriate drivers. For video cards, it loads the open source driver for the card it detects,  For Nvidia cards, that's the "Nouveau" driver.

For a number of reasons, Nouveau support is not strong for a number of Nvidia cards. (Nvidia does not release source code, etc.) In some cases, as you've found, the machine boots into a black and unusable screen.

Workarounds exist.  Follow the guidance in this thread -- [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) -- in the section headlined "How to enable kernel options on the livecd (before install)".  This outlines a procedure involving the passing of the "nomodeset" parameter to the kernel. With that, the kernel will be able to boot the machine with a sub-standard, but usable, display. At that point, you install a proprietary driver from Nvidia and reboot.

If your machine has onboard Intel video and if your BIOS allows you to set the machine to use ***only*** that Intel video, then do that and install Ubuntu. (Intel provides excellent support for Linux; an open source video driver provided by Intel will be used on boot if Intel video is active.)  Once you have Ubuntu installed, you can add the right proprietary driver from Nvidia.

Ubuntu includes an "Additional Drivers" tool which detects the Nvidia card in use and recommends a proprietary driver from Nvidia for installation,  After you select it, it downloads and installs that driver.  

You must be running on the Nvidia card before using "Additional Drivers". Otherwise, it can't detect the card.  You will need to use "nomodeset" to get a usable display for that.

---

### Post by 1clue on 2016-02-17
With respect to the Intel video card (which may or may not exist on your system), probably the easiest way is to yank your nvidia card out of the box during initial install, then install the nvidia proprietary driver, shut down and reinstall the nvidia card.

---

### Post by les11 on 2016-02-17
Thanks for the replies, i'll try using the Intel HD4600 iGPU for the initial instillation and putting the 970 back once those Nvidia drivers are installed, that to me seems the easiest way round the problem.

Failing that i'll try the kernel options, it looks complicated to me.

---

### Post by Geoffrey_Arndt on 2016-02-17
What you suggested Les, should work.   But if not, running the "nomodeset" boot option is actually quite simple - - here's one way (but there are two or three other methods):

[https://www.youtube.com/watch?v=jd9WIcPKc-o](https://www.youtube.com/watch?v=jd9WIcPKc-o)

---

