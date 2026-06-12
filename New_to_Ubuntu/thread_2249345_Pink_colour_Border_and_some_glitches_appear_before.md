---
title: "Pink colour Border and some glitches appear before starting Ubuntu 14.04"
date: 2014-10-21
forum: New to Ubuntu
---

### Post by christopher21 on 2014-10-21
Hello all,
    This is my first thread as i am new to linux and i chose ubuntu 14.04...I downloaded from the website and with the use of pendrive i installed it in my computer. Everything is good, except each time i start my Pc Pink colour border appears for nearly 3 seconds and followed by some glitches for 1 or 2 seconds and then i see ubuntu logo and the dots below that blinking and boots up and comes the password section and after that ubuntu desktop appears...
My question is "is it normal that i see that pink border and glitch everytime i startup or do i need to do something to avoid this?"
     Since i am new to Linux, i just fear that it has anything to do with my hardware...Please reply..


                                                                                                            Thank You 

My Pc Config
Gigabyte GA H61M-D2H
Intel Pentium G2020
Transcend 4Gb 1333Mhz
WD 1 TB HDD

---

### Post by BrunoLotse on 2014-10-21
Hi:) I've got the same problem and the same question when running 14.04.1.Cheers, Bruno

---

### Post by snowmobiler on 2014-10-21
Same here. I am not too concerned about it. Display is fine after boot-up. Will be reloading Ubuntu on an SSD in the laptop. Will updated if it goes away or same deal.

---

### Post by grahammechanical on 2014-10-21
We have to keep in mind that every Linux distribution, and Ubuntu is no exception, is made up of separate chunks of software written by different groups of developers. And so, during the loading of Ubuntu the process has to switch between some different chunks of code before it gets to the desktop. Consider.

1) the boot menu which uses the basic video of the motherboard BIOS/UEFI.
2) the Linux kernel begins to load and at first it is using the same motherboard video mode but it then loads the Xserver.
3) the Xserver loads either an open source video driver or a proprietary video driver according to our choice.
4) a splash screen appears. In Ubuntu it is called Plymouth.
5) a display manager takes over. In Ubuntu it is called LightDM (Light Display Manager) and we get a login screen.
6) after logging in a window compositor/manager is loaded. In Ubuntu it is called Compiz.
7) on top of Compiz a desktop environment (Gnome) and a user interface (Unity) are loaded. The user interface includes themes and background wallpaper.

It really is a complicated process and it is not easy to hide all that starting and stopping. This is life with Linux. At least until the Xserver, Lightdm and Compiz are replaced by Mir or a compositor based upon the Wayland protocol.

Oh, I forgot to mention. At some point the Xserver questions the monitor to find the optimum video resolution. 

Regards.

---

### Post by christopher21 on 2014-10-22
Hi..Thank u guys for ur reply..

---

### Post by haplorrhine on 2014-10-22
What?  The border isn't pink; it's purple, the same purple as my desktop wallpaper that fades from purple into pink.

---

### Post by snowmobiler on 2014-10-22
Does it with the new SSD I installed . . . just faster!:p

---

### Post by christopher21 on 2014-10-23
Pink or Purple color..Whatever...it appears

---

