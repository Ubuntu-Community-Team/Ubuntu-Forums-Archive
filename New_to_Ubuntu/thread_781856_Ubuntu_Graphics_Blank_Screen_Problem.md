---
title: "Ubuntu Graphics Blank Screen Problem"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by JoCoProductions on 2008-05-04
Hey guys just recently installed Ubuntu but I am getting graphical problems right after the Ubuntu loading splash screen is where the logon should be. The screen just turns an idle black and I think this is because I don't have the proper drivers for my Nvidia Geforce 6800. There is one way I can get into the dektop and that is if I edit my xorg.conf I can add vesa drivers and then it will work with no graphical effects applied. And from there is I try and install the drivers through EnvyNG it outputs this for me as an error.

```
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
```

Any fixes to this?

---

### Post by JoCoProductions on 2008-05-05
Maybe?

---

### Post by JoCoProductions on 2008-05-05
:(

---

### Post by Michl on 2008-05-05
For Nvidia you should first try System -> Admin _>
Hardware drivers and install the driver you need
that way.

Also, is this a problem you have with the live
cd, after you installed ubuntu or after you did
some of your own tweaking?

---

### Post by JoCoProductions on 2008-05-05
I did have graphics problems with the lice CD but, I got the alternate CD and it worked like a charm.

After I finished the install I booted into the desktop, enabled the sound and graphics drivers from system > admin > hardware drivers it seemed to work, I rebooted then right after the ubuntu loading bar splash screen my monitor (a 19" Dell flatscreen) goes black and the light turns orange.

I actually am beggining to think that the Nvidia driver thinks that I have a dual monitor setup because thats what it did on windows until I chose just to the setting clone because my only monitor was coming up for some reason as 2 (of 2) and it was being wierd. Is there any way I could check this out?

Right now I am in my ubuntu partition typing this and thats because I edited the xorg.conf and instead of Drivers    "Nvidia" I added "vesa" which seems to be a temporary fix.

Also how can I completely remove my drivers? I know I can go to System > administration and disable them, but is there a way I can completely uninstall them?

---

### Post by JoCoProductions on 2008-05-06
:(

---

### Post by Michl on 2008-05-06
I guess I wouldn't trust my own editing of
xorg and do in the terminal:

 ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Before I do that, I would unplug any devices I don't want
used, e.g. a second monitor.

---

### Post by vapotrini on 2008-05-06
Hmmm, you don't by chance have your computer hooked up to another display do you? Like a plasma tv? Had this same problem is why I ask... I'd forgotten my tv was hooked up.

---

### Post by JoCoProductions on 2008-05-06
Reconfiguring xorg didnt work and no I have never had or do I have a second monitor or TV hooked up to my computer :(

---

### Post by Michl on 2008-05-07
Well, this is a stab in the dark.  Log in the 
way it works and search for displayconfig-gtk
in synaptic.  Install and run it (from the
terminal, entering displayconfig-gtk.  There
you will have a chance to try out various
drivers and screen settings.  Just a warning,
the test function on displayconfig-gtk has
given me problems.  On some settings the
test will give you a blank screen even
though the settings are good.  Displayconfig-gtk
rewrites xorg for you.

For what it is worth, I don't have good experiences
with ubuntu's screen effects.  For me it messes-up
too many other things, so I never use them.

---

