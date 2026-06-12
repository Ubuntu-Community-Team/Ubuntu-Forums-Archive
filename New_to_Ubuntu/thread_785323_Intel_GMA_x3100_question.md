---
title: "Intel GMA x3100 question"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by TechDragon on 2008-05-07
How do I tell if ubuntu is using the right driver for this card?  It used to be in xorg.conf but now it does not appear to be there.  

How do I get this ubuntu to serve up dual monitors using this video card solution?  I used to use the "screens and graphics" tool but it is now hidden for good reason.  I can't use it without totally screwing the whole thing up.

This all used to work in 7.10 and I had hoped that they had changed for the better in 8.04 but without the ability to do dual monitors it is a show stopper for me.

IBM t61 integrated gma X3100 with dual 19" lcd monitors attached to a docking station.

Ubuntu 8.04 

why is it so f$#@%n hard to get dual monitors working correctly with Linux?

---

### Post by Starke on 2008-07-25
I`m trying to configure x3100 with dual monitor. I see that you get it solved. Can you paste your xorg.conf for me pls?

---

### Post by ET! on 2008-07-25
did you check the intel site for a linux driver????

---

### Post by Starke on 2008-07-28
Well, if you mean [this]("http://www.intellinuxgraphics.org/dualhead.html") site, it works perfectly for both statically and dynamically configuration. But what it does is, that it simply stretches one virtual desktop onto two monitors. 
  I can live with stretched wallpaper, but I do not know how to configure, which desktop is primary (showing menu bars), and which is  secondary. At least solving this issue will help. 
  Another thing is, that the center of this virtual desktop is somewhere between the two monitors, and pop-up windows and some applications are centering themselves into this location.

 This guide simple do not create extended desktop. Displayconfig utility promises this feature, but it generates xorg.conf all messed up with no chance to boot into X correctly.

 Is there any other way, how to create fully working (Windows like) extended desktop with menu bars on both screens on Intel graphics?

thanks for your help

---

