---
title: "How do i set the horizontal sync rate for hardy?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by khr on 2008-05-03
When i play 3D games there blinks really thick black lines all around the my screen. The thick black lines blink in a random places and they're always horizontal. I was thinking that i have to set my correct horizontal sync rate to fix it... But i don't know how to do that in Hardy! So how do i set the horizontal sync rate in hardy?

Please help!

---

### Post by artir on 2008-05-03
If yo have a nvidia, try sudo apt-get install nvidia-settings

---

### Post by khr on 2008-05-03
> **artir said:**
> If yo have a nvidia, try sudo apt-get install nvidia-settings

Im not using Nvidia, im using ATi.
ATi Mobility Radeon x1600

Edit:
I have ATi Catalyst control center Linux edition, but it gives me no option to change the horizontal sync rate...
Edit2:
I've also tried _sudo dpkg-reconfigure xserver-xorg_ but it only asks for language and keyboard language and stuff that has nothing to do with my screen.

---

### Post by khr on 2008-05-03
Anyone?

---

### Post by Cap'n Redbeard on 2008-05-03
> sudo displayconfig-gtk

runs a little display configuration app. in Hardy which offers lots more settings than the system/preferences/screen resolution preferences panel.

Please be careful with settings though - wrong sync rate, resolution, driver selection etc. could damage your telly.

:)

---

### Post by khr on 2008-05-03
> **Cap'n Redbeard said:**
> runs a little display configuration app. in Hardy which offers lots more settings than the system/preferences/screen resolution preferences panel.

Please be careful with settings though - wrong sync rate, resolution, driver selection etc. could damage your telly.

:)
```

sudo displayconfig-gtk
``` Opens a window where i can change the screen model, i chose "LCD 1280 x 800 Wide screen" and restarted...
When i started up ubuntu everything was just fine but the 3D games still are the same.

Anyways, thanks.

If you have any other ideas on how to get it to work, please help!

PS: I'm not sure if its a wrong horizontal sync rate(If it even is wrong) thats causing the thick blinking lines...

---

### Post by khr on 2008-05-03
Bump...
I really wanna play beautiful games without melting my eyes!

Please help!

---

### Post by sailor2001 on 2008-05-03
go to:  /usr/share/applications/screen&graffics

---

