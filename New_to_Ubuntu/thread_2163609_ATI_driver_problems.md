---
title: "ATI driver problems"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by OrhpSec on 2013-07-19
Hello everyone :) I am here to ask for some guidance, this is my first Ubuntu main install and I am having trouble getting my video driver to work. 

I'm running Ubuntu 12.10
Radeon HD 7770 is the graphics card

When I Install the drivers through 'Additional Drivers' I get a blank screen when I try to reboot the computer. There are several options in the 'Additional Drivers' window. #1 Experimental AMD binary Xorg driver and kernel module #2 AT?AMD proprietary FGLRX graphics driver(post-release updates)
and a third driver called (**experimental**beta) that I havent tryed. Both the first 2 drivers caused the Operating System to not boot back up.


I followed a tutorial on the subject, and it suggested to use the terminal.

```
sudo apt-get purge fglrx
```
followed by
```
sudo apt-get install linux-headers-generic
```

then the final step was to navigate to System Settings\Software Sources. Here is where I had to stop cause I couldn't find a program in 'System Settings' called Software Sources.


Hopefully that wasn't too redundant, and thanks for any and all advice.

---

### Post by QIII on 2013-07-19
Hey**,** OrhpSec!

And...

You are left with a black screen.

OK.

You can install the driver from the command line.  Fear not.  We often give instructions in the command line because it is common to all desktop environments and so it is easier to  cut through the jungle easily.

Ready?

---

### Post by OrhpSec on 2013-07-19
Yes, give it to me :)

---

### Post by QIII on 2013-07-19
OK.  Reboot your machine and hold the Shift key down immediately after you see the BIOS splash.

Keep holding it down until you see the GRUB screen (a menu of selections).

Use the down arrow to get to a line that says "Recovery" and choose that by pressing Enter.

You'll see a bunch of unintelligible text scroll by.  Don't try to read it.

Eventually, you'll get to another menu.  One of the selections will be something like "Drop to root prompt" or "root" (it changes every so often.  I don't remember what it was in 12.04)

Let me know when you are at the command prompt.

---

### Post by OrhpSec on 2013-07-19
KK sorry for the delay, I rebooted and now I am at a screen with the selections, hitting the recovery mode. I have a screen now that looks like it is loading drivers, it is flashing none stop 

```

udevd[329]: timelout: killing 'sbin/modprobe -bv pci:v00001002d0000683Dsv00001787sd0000201Cbc03sc00i00' [386]

```

the pinkish recovery screen popped up, and the above line repeated it self over top of it, and eventually pushed it off the screen

---

### Post by QIII on 2013-07-19
Let me know when you are at the command line.

I may not be right there with a response, since I'm also moderating.  Please be patient!  ;)

---

### Post by OrhpSec on 2013-07-19
No problem, I am more then thankful for the help thus far.

I rebooted and it is still getting hung up, it looks like it gives a stack trace before repeating

```

udevd[329]: timelout: killing 'sbin/modprobe -bv pci:v00001002d0000683Dsv00001787sd0000201Cbc03sc00i00' [386]
```

the screen pops up and I am able to scroll down to get a root shell, but the above line keeps repeating so fast that I cant type anything into the prompt.

---

### Post by QIII on 2013-07-19
Errrgh!

There's a bug about that on Launchpad.

What is your motherboard OEM and model?

It's late where I am, so I'm not sure I'll finish this, but there are a lot of other folks that can help -- patience!  :)

---

### Post by OrhpSec on 2013-07-19
No problem, its an Asrock z75 pro3 with a quad core ivy bridge 3570

---

### Post by OrhpSec on 2013-07-19
Ok, I am at the rootshell.

---

### Post by mastablasta on 2013-07-19
you said you have 12.10 but you have 12.04.

now go and try 13.04 and then install the drivers from additional drivers. 13.04 has a much newer kernel. and in linux drivers and such are part of kernel. the additional drivers should also attempt to install newer drivers for your card.

ofcourse oyu might get it all running with 12.04 but it will probably take more work/time.

---

### Post by OrhpSec on 2013-07-19
No, that sounds good, I just noticed and was going to ask. lol I just got rootshell finally

---

### Post by QIII on 2013-07-19
OK.  Log in with your username and enter your password when prompted.

---

### Post by axenic on 2013-07-19
If it's not much of a inconvenience, i'd recommend you to do a fresh install and install the graphical driver the way i will say below, it will most likely work.


    sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
    sudo apt-get autoclean
    sudo reboot
    sudo apt-get update
    sudo apt-get install fglrx-amdcccle-updates
    sudo aticonfig --initial
    sudo reboot

Regards,

Richard.

---

### Post by QIII on 2013-07-19
The need for a fresh install is rare and it is a solution often rushed into as a knee jerk.  I have, to my recollection, found it necessary to ask someone to reinstall fewer than 5 times.

If able to get to the command line, this can likely be solved without a reboot

---

