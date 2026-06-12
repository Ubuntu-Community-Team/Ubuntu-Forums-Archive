---
title: "Laptop suspend discovery! fix on its way?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by tsantsa31 on 2008-05-04
To set this up, I have an HP dv4000 series laptop on which I've just installed hardy heron a couple of days ago.  I have gutsy on my desktop (dual boot) and on my ps3 (which i don't use at all...)

Ok, so like many people I have the suspend when lid closed problem.  Ie, it will turn off the backlight, but leave everything else on.  This can be a serious issue if one were to put the laptop in a bag and it overheats...

So anyway, I have been hunting all over for a cure, but have yet to find one. I have discovered one thing.  I edited the acpi-support file (/etc/default) and commented out this line:  #ACPI_HIBERNATE=true

The line before this was ACPI_SLEEP=true.  I surmised that the laptop couldn't differentiate between both settings being true so one had to go.

Well, no luck.  HOWEVER. My laptop has a little button/tab thingy that triggers the lid closed behaviour (if working properly that is!).  I was just messing around with it and noticed, again, how it simply turns off the backlight.  Well I pressed it twice quickly. Double-Clicked it and lo and behold, my system went to standby!  

What I do for the meantime is press the button once then quickly close the lid and it remains in standby mode until I open the lid.  I don't really know if the commented out section is what did it, but I thought I would post it.  It seems to go into standby mode if I unplug the ac power while its on though, but if we put our heads together maybe we can get this whole thing resolved!

Did I do good?  :KS

---

