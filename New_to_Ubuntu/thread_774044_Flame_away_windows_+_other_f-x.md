---
title: "Flame away windows + other f-x"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by diaz028 on 2008-04-29
How do I get a window to flame/burn away when I click "x" ? 

Is there a place where I can go to find out about all those neat effects?

-D

---

### Post by PartisanEntity on 2008-04-29
Do you mean the Compiz desktop effects?
This might help:
[http://compiz.org/Documentation/Documentation](http://compiz.org/Documentation/Documentation)

---

### Post by laney on 2008-04-29
> **diaz028 said:**
> How do I get a window to flame/burn away when I click "x" ? 

Is there a place where I can go to find out about all those neat effects?

-D

If you install simple-ccsm then run "Simple CompizConfig Settings Manager" from System -> Preferences, you can find all sorts of options to change Compiz's behaviour. Look in "Animations" for the open/close/minimize animations.

---

### Post by teHIngo on 2008-04-29
The window manager that draws such nice effects "flame away windows" is named "compiz".
It comes with Ubuntu by default, however, you can only choose between "normal" and "extra" visula effects normally.

You may acces more options and customizable effects by installing the "compizconfig-settings-manager", accesible either via Synaptics or by copying "sudo apt-get install compizconfig-settings-manager" into the terminal. It will become available under "System --> Preferences --> Advanced Desktop Effect Settings". The option you are looking for can be found under "Animations."

Have fun!

---

### Post by billgoldberg on 2008-04-29
After you installed it, go to "system -> preferences -> advanced desktop effects settings."

Look for the "animations" button. Make sure the box next to it is ticked.

Then press the "animations" button.

Inside you need to look for "close animation". And then you'll see some effects enabled, like "glide 2" and "fade". Press the edit button and set the effect to "burn" for each of the mentioned effects in the "close animation" tab.

---

