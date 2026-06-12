---
title: "Make a sticky for Black Screen problem?"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by allwin on 2008-11-12
I cannot get the 8.10 Live CD to bring up a desktop.  I've tried changing to the VESA driver by altering my xorg.conf file.  I've tried the dpkg reconfigure stuff.  I've tried safe graphics.  All I get is NOT SUPPORTED message on my monitor (which is actually an HDTV hooked up to a KVM switch).  Even direct connect the monitor doesn't work.  WUBI fails the same way...after the UBUNTU progress bar, the system seems to be loading the desktop, the screen flashes, and goes blank, with the monitor complaining.

Search of Google reveals 29,000 hits on this problem.

No response from anyone on my earlier posts.

Shouldn't something this pervasive and this much of a show-stopper get a sticky so we can see when it's fixed?  I don't want to install an OS until I've seen if it will work, the WHOLE POINT behind the LiveCD.

---

### Post by bodhi.zazen on 2008-11-12
> **allwin said:**
> I cannot get the 8.10 Live CD to bring up a desktop.  I've tried changing to the VESA driver by altering my xorg.conf file.  I've tried the dpkg reconfigure stuff.  I've tried safe graphics.  All I get is NOT SUPPORTED message on my monitor (which is actually an HDTV hooked up to a KVM switch).  Even direct connect the monitor doesn't work.  WUBI fails the same way...after the UBUNTU progress bar, the system seems to be loading the desktop, the screen flashes, and goes blank, with the monitor complaining.

Search of Google reveals 29,000 hits on this problem.

No response from anyone on my earlier posts.

Shouldn't something this pervasive and this much of a show-stopper get a sticky so we can see when it's fixed?  I don't want to install an OS until I've seen if it will work, the WHOLE POINT behind the LiveCD.

I understand your frustration, but what would the sticky say exactly ?

The cause of this problem is quite varied and the solution is usually to either use compatible hardware or install the OS then install the drivers.

What videocard do you have ?

---

### Post by allwin on 2008-11-12
OK, it's not a video card, it's onboard.  Intel g33/g31 chipset.

How would I go about installing drivers for this via the LiveCD?

Remember, I can't paste commands!

Now, I did check the integrity of the CD and all that.  I was able to bring up a console and even browse the xorg log file but saw no obvious errors except one that said "error setting MTRR...code(21)".  Don't know if that's it, or what?

One thing is it seems to be using the fglrx driver, which I thought was for ATI cards...but I'm kind of a newbie here and don't know the names down cold or what's open source vs. proprietary.

---

### Post by bodhi.zazen on 2008-11-12
Well, "on board" is still a videocard.

I am not sure of a solution, but see if this helps at all :

[http://software.intel.com/en-us/forums/user-community-for-intel-graphics-technology/topic/60208](http://software.intel.com/en-us/forums/user-community-for-intel-graphics-technology/topic/60208)

---

### Post by binbash on 2008-11-12
I got mine working.


-Install ubuntu via alternate cd
-At startx it will fail.Alt ctrl f1 there and drop to terminal
-sudo apt-get update && sudo apt-get upgrade 
-REBOOT NOW
-Again drop to terminal after startx
-sudo apt-get install build-essential x11-drv-fglrx
-sudo aticonfig --initial
-REBOOT NOW

It will WORK : )

---

### Post by allwin on 2008-11-12
> **binbash said:**
> I got mine working.


-Install ubuntu via alternate cd
-At startx it will fail.Alt ctrl f1 there and drop to terminal
-sudo apt-get update && sudo apt-get upgrade 
-REBOOT NOW
-Again drop to terminal after startx
-sudo apt-get install build-essential x11-drv-fglrx
-sudo aticonfig --initial
-REBOOT NOW

It will WORK : )

Thanks, I may try that BUT one question.  The driver you mention above is fglrx.  Does this driver work with an Intel GMA?  That's one thing that confuses me.  I think it should be one of the Intel drivers I download and rebuild from somewhere.

Does fglrx actually work with Intel chipsets?

---

