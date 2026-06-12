---
title: "ok my sound isent very loud"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by Kedster on 2008-05-03
ok so in gutsy when i installed there was no sound so i had to 

The sounds wasn't working. I fixed it by pasting:

Code:

options snd-hda-intel model=auto

at the bottom of:

Code:

/etc/modprobe.d/alsa-base

and it would work awsome (exept the speaker would still make sound when headphones were pluged in)

but now with hardy the sound works right form install but is very very low

---

### Post by Kedster on 2008-05-03
i no that on fiesty it didnt work at first and now its low so is it something that i could chaange

---

### Post by WiFi Ed on 2008-05-03
Mine was very quiet also, but this fixed it for me:

Right-click on the speaker icon in the top bar, choose Open Volume Control.

On my pc, the "Front" volume sliders were at about 80%, I slid them up to the top and now I have normal sound levels.

---

### Post by jbulmer08 on 2008-05-03
what it could be is the power settings. in the way that with the new version the code has set the output power to a sertin levle which is less than the old ubuntu. This was the case with my sd card but i dont know how to fix it

---

### Post by Kedster on 2008-05-03
well this really sucks cuz my comp is my music player

---

### Post by Kedster on 2008-05-03
please

---

### Post by Tom--d on 2008-05-03
In terminal, type:

```
gnome-volume-control
```

and make sure all bars are full.

---

### Post by Kedster on 2008-05-03
ya there all full

---

