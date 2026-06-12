---
title: "dual display, different resolution"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by wmmutch on 2013-04-08
my sys is a dual boot, Win Sys7 and Ubuntu 12.04 LTS updated today.  I have two monitors, a Dell LCD @1280 x 1024 and a Nokia CRT 446Xpro @ 1600 x 1200.  The monitors are driven by a 32 bit Radeon X300/X1050 series PCI adaptor.  In Win Sys7 th driver is MS WDDM.  Under Win Sys7 the dual monitor display works fine in all respects, so all hardware is A-OK. This is a software issue.   When booted to Ubuntu both monitors initially display the same startup, but once boot is complete the Nokia remains black with no evidence of signal.  The System Settings/Displays screen shows only the Dell and is unable to detect the Nokia.  Running xrandr in Xterm says DVI-0 is disconnected (normal left inverted right) and DVI-1 (the Dell) is connected and @1280 x 1024. (normal left inverted right.)

How do I get DVI-0  connected and working properly ???

---

### Post by wmmutch on 2013-04-08
my sys is a dual boot, Win Sys7 and Ubuntu 12.04 LTS updated today.  I  have two monitors, a Dell LCD @1280 x 1024 and a Nokia CRT 446Xpro @  1600 x 1200.  The monitors are driven by a 32 bit Radeon X300/X1050  series PCI adaptor.  In Win Sys7 th driver is MS WDDM.  Under Win Sys7  the dual monitor display works fine in all respects, so all hardware is  A-OK. This is a software issue.   When booted to Ubuntu both monitors  initially display the same startup, but once boot is complete the Nokia  remains black with no evidence of signal.  The System Settings/Displays  screen shows only the Dell and is unable to detect the Nokia.  Running  xrandr in Xterm says DVI-0 is disconnected (normal left inverted right)  and DVI-1 (the Dell) is connected and @1280 x 1024. (normal left  inverted right.)

How do I get DVI-0  connected and working properly ???

---

### Post by Habanero101 on 2013-04-08
You can try disconnecting the detected display - the Dell LCD, and reboot with only the Nokia CRT connected to try to force the OS to use and see the Nokia CRT and then if that works, reconnect the Dell LCD and try the 'Detect Displays' on Display screen and configure from there.

If that doesn't work, try installing new linux ATI drivers for your card from ATI.
Try:
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
or
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

---

### Post by mörgæs on 2013-04-08
Please don't double-post.
Merged.

---

### Post by wmmutch on 2013-04-08
TNX habanero101   I can now see both monitors and will try to bring resolution of the Nokia up from 1024 x 786 to  1600 x 1200.

Sorry about duplicate post.  I started in the hardware sub-forum and realized it was a software issue.  I'm new to Ubuntu.  I volunteer at Fingerlakes Re-Use where everyone else uses it...so I have to learn.

---

