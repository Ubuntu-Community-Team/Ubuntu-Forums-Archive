---
title: "hmmm. Upgrade to 8.04 went fine but..."
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Dano30 on 2008-04-27
Ok so I upgraded to 8.04 and it works great except for one glitch.  It seems that my left mouse button is acting like it is being double clicked every time I try to use it.  I'm unable to launch an application from the panel unless I right click it and use the "Launch" menu item in the context menu. I cannot keep a menu active unless I hold down the left mouse key while I am navigating. If I try to move the calendar ahead one month, it moves ahead two.   Anybody got any Ideas ???

---

### Post by MaindotC on 2008-04-27
Can you try a different mouse just to eliminate that possibility?

---

### Post by Dano30 on 2008-04-27
Yep. Tried that but had the same results with both devices.

---

### Post by Dano30 on 2008-04-28
OK. Seems that for some reason the wrong mouse configuration was written into the xorg.conf file. I changed it to the old configuration and all is well.

---

