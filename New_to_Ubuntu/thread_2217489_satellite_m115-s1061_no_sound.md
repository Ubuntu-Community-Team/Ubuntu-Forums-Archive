---
title: "satellite m115-s1061 no sound"
date: 2014-04-17
forum: New to Ubuntu
---

### Post by Robert_Turner on 2014-04-17
I just installed ubuntu 12.04 on a satellite m115-s1061 and I have no sound.

Please advise.

Thank you.

---

### Post by ajgreeny on 2014-04-17
Two things to do for a start.


[LIST=1]
[*]Run the command  **alsamixer** in terminal and check that the levels of outputs are not set too low.
Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.
[*]Click on the volume icon in your panel and then on Sound Settings (or similar description) which should open the **pulseaudio-volume-control** and you may find something is muted or set too low.
[/LIST]

---

### Post by Mama_Hadija on 2014-04-18
download drivers using update package

---

