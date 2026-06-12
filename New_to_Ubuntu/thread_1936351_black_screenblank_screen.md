---
title: "black screen/blank screen"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by Saintkilla on 2012-03-05
hello i burned a ubuntu iso to a disc earlier and i went to install it worked fine... and then it ejected the tray and rebooted the grub menu showed and (im dualbooting) 3 options came up ubuntu, ubuntu recovery, and windows 7 when i press ubuntu it shows a black screen with backlight then just shows a blank screen backlight off


Any help could be useful thanks


~Michael

---

### Post by kevdog on 2012-03-05
Its a video driver thing for sure.  If you press F1 during this blank screen, it should drop you to a terminal.  Troubleshooting video cards in my opinion are a Pain in the A**. However, just some words of advice, --- know your hardware really well -- might need to boot to windows to find this info, and then do a search on how to install the driver for your hardware, or your monitor, or how to configure the xorg.conf file.  Yes its a pain in the butt!

---

### Post by EngineersGarage on 2012-04-30
i have same problem... i know how to get the screen on(backlight)...

in terminal, as root. insert this code: setpci -s 00:02.0 F4.B=00

then go:

nano /etc/rc.local -enter.

then a window pops up with some txt in it. at the bottom you insert " setpci -s 00:02.0 F4.B=00 "
(exit 0 must be the last line)

press F3 to write
press Ctrl-x to exit

then when pc boots up the backlight will come on.. 

im still figuring out after pc goes to sleep,the screen stays black... its more code you have to insert but cant remember...still searching..

Will.

---

