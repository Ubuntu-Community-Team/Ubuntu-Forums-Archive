---
title: "Gnome Power Manager problem"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by jerrynewt on 2011-12-23
I keep getting this info block at the top right of my screen 
"Install Problem! The Configuration defaults for Gnome Power Manager have not been installed correctly. Please contact your computer administrator." and then the screen goes black. I have to hold the power button to shut the comp off. I am running Zorin 5.0 on a Toshiba Satellite Pro 6100 -- 768 Megs ram -- 250 Gig HD.
  I can't seem to figure out how to boot into recovery mode to do an upgrade. I have tried hitting Esc, f2, f8, f10, f12, and Shift during power up, but so far it just boots to regular boot screen--then the information block described above--then black screen. I have also tried to boot from live cd but for some reason it will not read the cd, even with the boot sequence set to boot from cd. There is no option for booting from usb stick either. Kind of stuck on this one for bout two weeks now and I sure could use some help. Thanks in advance and Merry Christmas to everyone on the forums--you have been getting me thru ubuntu since 2006 and I have loved every minute of it.

---

### Post by ExileAmongYou on 2011-12-23
To get into recovery mode, you hold down Shift while GRUB is starting. When your computer starts up, the first thing you usually see is your motherboard/BIOS's startup screen, and then after that disappears, GRUB starts.
So, you want to press and hold shift *after* that first screen goes away.

---

### Post by jerrynewt on 2011-12-23
When grub comes up and I boot into recovery mode it goes thru all of the boot processes and then goes to

[   2.055441] Console: switching to colour frame buffer device 80x30

under this line is a blinking cursor only. No login info at all.

---

### Post by jerrynewt on 2011-12-24
bump**

---

### Post by jerrynewt on 2011-12-25
bump**

---

### Post by jerrynewt on 2011-12-26
bump again **

---

### Post by meditatingfrog on 2011-12-26
> **jerrynewt said:**
> I keep getting this info block at the top right of my screen 
"Install Problem! The Configuration defaults for Gnome Power Manager have not been installed correctly. Please contact your computer administrator." and then the screen goes black. I have to hold the power button to shut the comp off. I am running Zorin 5.0 on a Toshiba Satellite Pro 6100 -- 768 Megs ram -- 250 Gig HD.
  I can't seem to figure out how to boot into recovery mode to do an upgrade. I have tried hitting Esc, f2, f8, f10, f12, and Shift during power up, but so far it just boots to regular boot screen--then the information block described above--then black screen. I have also tried to boot from live cd but for some reason it will not read the cd, even with the boot sequence set to boot from cd. There is no option for booting from usb stick either. Kind of stuck on this one for bout two weeks now and I sure could use some help. Thanks in advance and Merry Christmas to everyone on the forums--you have been getting me thru ubuntu since 2006 and I have loved every minute of it.

Have you tried going into another tty (ctrl-alt-f1) and killing gnome-power-manager instead of rebooting?  It isn't a fix, but i believe it's a step in the right direction.

---

