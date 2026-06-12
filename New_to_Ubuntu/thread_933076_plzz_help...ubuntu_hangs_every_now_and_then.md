---
title: "plzz help...ubuntu hangs every now and then"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by ravikanwal on 2008-09-29
Hi, 

I'm new to ubuntu .. installed super ubuntu  just 2 days back (shifted from vista ultimate)... i don't know wat happens but the hard disk seems busy, wifi signal blinks(as normal and downloading), pressing the bluetooth button on laptop also turns its blue light on but everything on screen just freezes...i've tried pressing all different keys, but have to restart it using the power button..plzz help..

also 1 more silly lil question..saw d fire effect in a video on youtube...super ubuntu comes wid compiz fusion..how do i activate dat fire effect( the window starts burning on clicking the X )

---

### Post by kpkeerthi on 2008-09-29
Turn off Visual Effects from System -> Preference -> Appearance -> Visual Effects and see if that improves stability. The most common cause of freezes in Linux are graphics drivers.

---

### Post by kpkeerthi on 2008-09-29
Also post the output of ```
lspci
``` command so we can take a look at your hardware details.

---

### Post by ravikanwal on 2008-09-29
i'm in office rite now...will do dat wen i get back home( hv installed it on my personal laptop)...Ny advice on the fire effects???

---

### Post by kpkeerthi on 2008-09-29
1. Enable Visual Effects from System -> Preference -> Appearance -> Visual Effects and make sure it does work.

2. Install compizconfig-settings-manager  
```
sudo apt-get update && sudo apt-get install compizconfig-settings-manager 
```

3. Press ALT + F2 and type **ccsm <enter> **or launch it from the Preferences menu.

4. Enable the Animation plugin and activate the 'Burn' effect.
See [http://wiki.compiz-fusion.org/Plugins/Animation](http://wiki.compiz-fusion.org/Plugins/Animation) for more information.

---

