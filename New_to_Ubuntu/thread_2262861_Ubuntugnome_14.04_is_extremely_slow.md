---
title: "Ubuntugnome 14.04 is extremely slow"
date: 2015-01-27
forum: New to Ubuntu
---

### Post by regonzalom on 2015-01-27
I'm an old ubuntu user but I'm not an expert (I can make it work but always looking on internet).


Recently I installed ubuntugnome 14.04. At the beginning all seemed ok, but eventually Ubuntu slowed. Now some of my applications starts in 10 seconds!!! and I have to wait 3 minutes before to work when my system is start (My programs simply do not start in that span and after that, they open all together). 


> 

-Computer-
Processor        : 8x Intel(R) Core(TM) i7-3612QM CPU @ 2.10GHz
Memory        : 8045MB (2484MB used)
Operating System        : Ubuntu 14.04.1 LTS
User Name        : gon (gon)
Date/Time        : mar 27 ene 2015 21:14:38 ART
-Display-
Resolution        : 2390x768 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA Intel PCH
-Input Devices-
 Power Button
 Sleep Button
 Lid Switch
 Power Button
 AT Translated Set 2 keyboard
 Logitech USB Optical Mouse
 Video Bus
 Video Bus
 ALPS PS/2 Device
 AlpsPS/2 ALPS GlidePoint
 HDA Intel PCH HDMI/DP,pcm        : 3=
 HDA Intel PCH Headphone
 HDA Intel PCH Mic
 Dell WMI hotkeys
 Laptop_Integrated_Webcam_HD
-Printers (CUPS)-
Epson-Stylus-TX125        : <i>Default</i>
-SCSI Disks-
ATA ST1000LM024 HN-M
TSSTcorp DVD+-RW SN-208BB
Generic- xD/SD/M.S.
SAMSUNG GT-S5570L Card






This is a summary of my system. I would appreciate any help.


Regards,
Gonzalo

---

### Post by kerry_s on 2015-01-27
have you looked at the system monitor see if anything is running.
are you using lots of extensions ?

i use the systemmonitor extension on mine for fast access.

---

### Post by buzzingrobot on 2015-01-27
> **regonzalom said:**
>  (My programs simply do not start in that span and after that, they open all together). 


A long delay like that when the system boots could be due to repeated attempts to start a service, connect with the network, or something else that should run at startup but, for some reason, either is not running and eventually timing out or taking several minutes to launch.

You might check if the network is up without delay after a reboot -- does the browser work?, as well as disabling any Gnome extensions and all startup applications.  If the system boots normally after that, then re-enable extensions/startups one at a time until the culprit is found.


.

---

