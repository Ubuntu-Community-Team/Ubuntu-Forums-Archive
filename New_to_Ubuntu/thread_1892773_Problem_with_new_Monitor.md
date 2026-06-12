---
title: "Problem with new Monitor"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by colt66 on 2011-12-08
I just got a new LG Flatron e2241 and when I connected it to my 10.4 ubuntu Is shows everything without a problem until I get to the login screen.  Instead of showing the login screen the monitor shows auto adjust then goes black.  I have tried restarting the monitor and reinstalling ubuntu. If I start ubuntu with my old monitor then switch to the Flatron it shows everything fine but I don't want to do that every time I boot up.  Any help would be greatly appreciated.

---

### Post by pqwoerituytrueiwoq on 2011-12-08
force the resolution in xorg.conf
if yuo have a nvidia gpu use nvida settings to do this (much easer)
[FONT=Courier New]gksu nvidia-settings[/FONT] use the save to xorg config file button

---

### Post by wolfen69 on 2011-12-08
> **pqwoerituytrueiwoq said:**
> force the resolution in xorg.conf
if yuo have a nvidia gpu use nvida settings to do this (much easer)
[FONT=Courier New]gksu nvidia-settings[/FONT] use the save to xorg config file button

The OP can't even get to the login screen. That will not work.

---

### Post by fantab on 2011-12-08
> **colt66 said:**
> I just got a new LG Flatron e2241 and when I connected it to my 10.4 ubuntu Is shows everything without a problem until I get to the login screen.  Instead of showing the login screen the monitor shows auto adjust then goes black.  I have tried restarting the monitor and reinstalling ubuntu. If I start ubuntu with my old monitor then switch to the Flatron it shows everything fine but I don't want to do that every time I boot up.  Any help would be greatly appreciated.

Since its a "new LG Flatron e2241", I suggest you consult the Monitor's User Manual. AFAIK you have to do some basics, like connect the cable, power on  and let the monitor do its Auto-Audjustment. Also check the monitor with other OS on other computers to make absolutely sure that its not the Monitor itself at fault.

---

### Post by pqwoerituytrueiwoq on 2011-12-09
> **wolfen69 said:**
> The OP can't even get to the login screen. That will not work.
he has his old monitor he can use he said he could swich back and forth to use it as it is now

---

### Post by colt66 on 2011-12-09
> **pqwoerituytrueiwoq said:**
> force the resolution in xorg.conf
if yuo have a nvidia gpu use nvida settings to do this (much easer)
[FONT=Courier New]gksu nvidia-settings[/FONT] use the save to xorg config file button
That didn't work. Any other suggestions? Thanks for your help.

---

