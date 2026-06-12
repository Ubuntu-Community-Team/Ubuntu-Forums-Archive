---
title: "Bar shadows"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by TheSlipstream on 2008-07-09
Does anyone know how to remove the shadow dropped by the top bar (as in Applications Places...)? It's messing up my theme. :P

---

### Post by NovaAesa on 2008-07-09
If your are using Compiz Fusion (AFAIK you should be by default?), then you can change it with ConpizConfig Settings Manager. The setting is under "Window Decoration". You should either set the Shadow Radius to 0, or change the Shaddow Opacity to 0.

---

### Post by TheSlipstream on 2008-07-09
Thanks, but I tried it and it doesn't work. I'm not sure the bar at the top that has all the shortcuts is covered by Window Decoration.

---

### Post by tjwoosta on 2008-07-09
that shadow should be covered in window decoration


do you have emerald theme manager running?

if you are using an emerald theme the go to "system-preferences-emerald theme manager"  then click the edit themes tab then the frames and shadows tab

---

### Post by ad_267 on 2008-07-09
Hi, I've done this.

Open up compizconfig-settings-manager. Go to the Window Decorations settings. Click on the + next to Shadow Windows and select Window Title for the type. Click Grab and then click on your panel. Relation should be And and Invert should be ticked.

This will only disable shadows for the panel and not for any other windows. If you want to disable this for all windows just delete "any" from the "Shadow Windows" line.

---

### Post by TheSlipstream on 2008-07-09
Yep, that was it. Mucho thanko. :D

---

