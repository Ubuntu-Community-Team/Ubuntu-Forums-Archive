---
title: "Video card problem with Ubuntu 8.04"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by walarson on 2008-04-28
I am running a stock Dell Dimension 2350 with an integrated Intel (i810 is what I usually use) video card.

With Ubuntu 8.04 desktop I have the following problems.  When it starts up, the screen is completely black until the X-window-system comes up.  If I try to change the desktop to 1024x768 (because of problems reading smaller type), the X-window-system goes completely black and I am no longer able to see anything.  Finally, the console (control alt F1-etc) fonts are gigantic.  As an example, the command pwd takes up about 1/4 to 1/2 of the screen real estate in an ordinary console.

None of these problems occurred with Ubuntu 8.04 beta desktop.  I have had these same problems with earlier versions of Ubuntu and for this reason have never used it but remained with Debian Sarge.  I'd like to upgrade to more recent software though.

---

### Post by tgape on 2008-06-27
If the fonts are that large - verify that 1024x768 is actually a smaller resolution than what the system is picking by default.  It could be that 8.04 fails to recognize your hardware such that it's failing over to bog-standard VGA 640x400 support.  (I can't verify how to do this at the moment, as my computer recently died a painful video adapter death a couple days ago, despite only being a few weeks old.)

If that's the case, and if aptitude or synaptic do not offer an alternate X driver for your hardware, then I have no easy answer for you.

That having been said, you should probably check out the repository for a hardware-specific X driver that matches what you have.

---

### Post by anderskitson on 2008-06-27
THe only thing I can think of is assigning more memory to your card in the bios, I had a problem with certain resolutions before, and this solved it. As well as using the command 
> sudo dpkg-reconfigure xserver-xorg
and then assign different amounts of memory to play with

---

