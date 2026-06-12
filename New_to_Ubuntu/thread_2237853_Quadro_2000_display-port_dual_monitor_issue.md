---
title: "Quadro 2000 display-port dual monitor issue"
date: 2014-08-04
forum: New to Ubuntu
---

### Post by keith27 on 2014-08-04
Ubuntu 12.04 w/ native Unity desktop
Quadro 2000 - VBIOS=70.06.3f.00.01
Driver= 304.116 OR 331.20
Hardware is a Xeon Lenovo S20 w/ 8GB. 

Primary monitor is on DVI
Secondary monitor is on DisplayPort

If I do anything that resets the video driver (starting or restarting the box, starting most screensavers, fullscreen video) then the output to the displayport is shut off. Primary monitor is fine. Secondary monitor goes dead until I pull and reseat the displayport wire. Power cycling the monitor does not make a difference. When I reseat the displayport the output is right back on where I left it. No fuss. But re-seating the cable every time a screensaver or video player kicks off is obviously not ideal. 

I've tried all four permutations of drivers that Ubuntu points to (304, 331, 304-updates, 331-updates) and all have the same behavior. 

Anyone out there with similar issues on a Quadro 2000 or with DisplayPort output?

---

### Post by keith27 on 2014-08-22
Upgraded to 14.04 and there are now more triggers that cause the DisplayPort to die. Either going to a new video card or a new OS soon. The 14.04 "online search" features are really annoying (killed already - but can't say I can recommend Ubuntu to novices anymore.)

---

### Post by buzzingrobot on 2014-08-22
The Nvidia drivers are supplied as binary blobs from Nvidia, so they're going to be the same on any distribution. Kernel configs can make a difference. (E.g., Nvidia drivers in combination with any Arch or Arch-derivative kernel boot here to a black screen and dead keyboard, but work fine in Ubuntu, Fedora, etc..) 

I have a ThinkPad W530 with a Quadro.  Don't use a secondary display, but I do recall seeing a few pages offering guidance on getting them to work on Linux with a second display. (Apparenly, they're fussy about it.)

Re: online search -- If you haven't already, install Unity Tweak Tool and disable the functionality in there. Also, the "FixUbuntu" site is still around, which downloads and runs  a shell script to zap the scopes. (It's all going to be opt in, not opt out, in 14.10).

---

