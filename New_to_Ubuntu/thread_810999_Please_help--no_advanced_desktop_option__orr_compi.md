---
title: "Please help--no advanced desktop option / orr compiz?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by circuitslave on 2008-05-28
First let me say, I searched the forum, but didn't get any result. 

I just installed the 8.04 LTS Desktop --with the Live CD option and I'm wondering how and why I can't get the desktop cube effect installed/working?

I did go into Add/Remove Software option and installed the compiz software. But I have no "Advanced Desktop Effect" settings option in Preferences at all to begin with. There's nothing except Appearance (which I did increase from Normal effects to Extra Effects).

I have wavy windows which can be pulled and stretch and such, but no other options.  My video card is an Radeon AIW x800xt, if that makes any difference.  There's no hardware drivers avaiable or nesessary it seems. 

What am I missing?  I believe compiz is installed because it shows in Synaptic options the different compiz component versions installed and listed.

Thanks for your help.

---

### Post by SunnyRabbiera on 2008-05-28
well in synaptic make sure to install the extra plugins packages and such

---

### Post by circuitslave on 2008-05-28
> **SunnyRabbiera said:**
> well in synaptic make sure to install the extra plugins packages and such


thanks for the tip. I'll try that--there's several; however,
shouldn't I still have "advanced desktop effect settings" listed as an option?

---

### Post by starcannon on 2008-05-28
Open Synaptic Package Manager and install *Compiz configuration settings manager*

A new menu item will then be available in *System-->Preferences-->Advanced Desktop Effects Settings*

That should get you going from what I can access from your op

---

### Post by SunnyRabbiera on 2008-05-28
well in hardy if you get all the packages needed the advanced desktop settings module should come up in the system menu under preferences.
I suggest you make sure the following packages are installed:
compiz
compizconfig-backend-gconf
compizconfig-settings-manager
compiz-fusion-plugins-extra
compiz-fusion-plugins-main
compiz-gnome
compiz-plugins
libcompizconfig0
libdecoration0
python-compizconfig

---

### Post by circuitslave on 2008-05-29
> **SunnyRabbiera said:**
> well in hardy if you get all the packages needed the advanced desktop settings module should come up in the system menu under preferences.
I suggest you make sure the following packages are installed:
compiz
compizconfig-backend-gconf
compizconfig-settings-manager
compiz-fusion-plugins-extra
compiz-fusion-plugins-main
compiz-gnome
compiz-plugins
libcompizconfig0
libdecoration0
python-compizconfig


ONE THING I DID NOTICE NOW IS COMPIZCONFIG-SETTINGS-MANAGER IS NOT LISTED IN THE SYNAPTIC MANAGER?  I only show "OpenGL window and compositing manager" ? hmmm..

By the way, should I be installing any ATI drivers from the repository? Would that make a difference first of all?

Btw,  Here's a screenshot if this helps also the Menu in Preferences, which doesn't have advance option:

---

