---
title: "New to Linux.  Have some problems after Ubuntu install."
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Jay03 on 2008-07-03
I just installed Linux Ubuntu on my computer and am having some issues.  I am totally new to Linux and don't know anything about the commands for the terminal.  This may be a big post but here it goes.

It seems like my sound isn't loud enough.  I have to turn it up almost all the way to hear anything.  I also noticed my mic doesn't seem to be working in Ubuntu.  Here are my specs:

ASUS M2N32-SLI Deluxe with WIFI
2GB of Ram
AMD x2 64bit 6000+
250GB SATA Hard drive
256MB Nvidia 8600GT Video Card

I'm using the onboard sound which is the Soundmax ADI AD1988B 8 channel codec.  I tried different selections in the sound properties but no change.  I also went into the volume controls and turned everything up.  

The sound was working good in Windows XP before I installed Ubuntu.  Is there a way to reset or reinstall just the sound?  Maybe its not installed correctly.

My next problem is the screen resolution is not detecting my Samsung Syncmaster 730B LCD monitor correctly after installing the Nvidia Proprietary Drivers.  It says Unknown and sets the refresh rate to 50hz instead of 60hz.  There is no option for 60hz.  I have a Nvidia 8600GT Video Card.  I also see that the fonts look blurry in Ubuntu but am not sure if its because of the resolution settings or drivers.

My next issue is my printer.  Ubuntu sees my Canon Pixma ip6220D printer but doesn't have a driver for it.  I mainly use it to print photos in Windows XP.

Also, is there a way to see all hardware components detected?  Something like Device Manager in Windows XP.  

Well thats it for now.  Thanks for any help.

---

### Post by Sef on 2008-07-03
1) It is best to put each problem in a single thread.

2) Looks at [OpenPrinting]("http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP6000d").  Note: it is the closest model I could find to your computer.

3) How did you install the NVidia drivers?

---

### Post by spiderbatdad on 2008-07-03
not sure, but you might check synaptic for other nvidia drivers...you may need the nvidia-glx-legacy driver.

to my knowledge there is nothing so fancy as device manager, but I may be wrong. To see connected hardware and drivers, you can run a few commands:

sudo lshw

lspci

lsusb

---

### Post by kansasnoob on 2008-07-03
As far as the sound problem try installing > gnome-alsamixer from synaptic.

It'll then show up in Sound & Video:

[ATTACH]76290[/ATTACH]

[ATTACH]76291[/ATTACH]

Sorry I can't help with the others:confused:

---

### Post by Jay03 on 2008-07-03
Thanks for all the replies.  I still couldn't get my sound or mic working correctly.  The printer also didn't print very well.  I'm currently formatting my hard drive to put a fresh copy of windows  XP on.  Until Linux installs correct working drivers with ease I think I will stick with Windows.  I like Ubuntu but its just not worth the headache to get everything working correctly, I also don't have time to learn all the commands for the terminal which can be confusing.

---

