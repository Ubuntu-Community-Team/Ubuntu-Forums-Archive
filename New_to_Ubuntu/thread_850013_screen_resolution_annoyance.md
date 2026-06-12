---
title: "screen resolution annoyance"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by le singe on 2008-07-05
Hello every and anyone.  I have a few questions about screen resolutions in Hardy Heron.

I have a 15/15.4 inch laptop display with some kind intel 945 express chipset, came with a centrino duo.  Is it likely that 1024 X 768 would be the maximum resolution?  

Thinking that I could surely go up closer to 1280 X 1024, I started messing with resolution and video card settings, selecting different resolutions of generic LCD displays, selecting plug and play, yet could not effectively get any resolution higher 1024 X 768.  What's frustrating is that after all this I can't figure out how to let ubuntu restore what it had set up as the defaults, which actually gave me a tad higher res (1280 X 800) and what seemed as less washed-out colors (refresh rate difference?)  Furthermore, under the screen resolution box, my display is no longer detected (now says "unknown" instead of "15 inch")  

Is there a way to let Ubuntu restore these defaults and redetect my display/optimum settings?  Hitting the "detect displays" does nothing either in the screen resolution setup or "screens and graphics."  Should I be able to attain a higher resolution?

---

### Post by bhavi on 2008-07-05
Try running this command as root and modifying screen resolution (press alt+f2 and enter)

```
gksu displayconfig-gtk
```

---

### Post by le singe on 2008-07-05
how do I enter the command as root?

---

### Post by suprfish on 2008-07-05
> **le singe said:**
> how do I enter the command as root?

Do (in a terminal)
```
 gksudo displayconfig-gtk 
```

It will prompt you for your password.

---

### Post by philinux on 2008-07-05
gksu will give you root.

It translates as gk graphical su sudo

---

### Post by le singe on 2008-07-05
Got it!

well, wolfen69 actually got it.  I searched similar problems and found this suggestion to another post:

in the terminal, type:
sudo dpkg-reconfigure -phigh xserver-xorg

then reboot.  For me, that reset the default display settings and again my laptop screen and optimal settings were recognized.  So, if anyone has the same issue, try that.

Thanks for the help.

---

### Post by Dr John on 2008-07-06
I have the same problem on my Intel D945GCLF motherboard.  It seems as if the Intel driver just doesn't work, period.  Whenever I try to change the screen resolution to match that of my display (1280 x 1024 LCD monitor) -- or any other resolution that it can display -- the driver crashes and eventually I get the application that goes through the reconfiguration process for me.  The only thing that works is to let the software choose the VESA driver.  With the VESA driver I can get the full 1280 x 1024 pixel resolution.  However, it suffers from all of the speed limitations accordingly.

I've tried every one of the suggestions mentioned in the previous posts and have used the "Screens and Graphics" application from the applications menu, all to no avail.

I'm using Ubuntu Hardy.  Any suggestions will be followed up.

---

