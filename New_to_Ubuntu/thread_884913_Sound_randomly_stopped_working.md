---
title: "Sound randomly stopped working"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Dark006 on 2008-08-09
I was using my computer yesterday and everything worked fine (including the sound). But for some reason when I got on today its now not working at all. Anyone have any ideas??

---

### Post by st33med on 2008-08-09
Have you checked your mute button?
If nothing works:
```
alsamixer
```
Unmute PCI and Master with the M key if they're muted and turn them up to somewhere around 70-90 for a safe range.

---

### Post by Bucky Ball on 2008-08-09
Right click the speaker icon and go to preferences. Is the right driver there? Experiment and try alsa. Try hitting the volume or mute button on the laptop (if you have one). Try;

System->Preferences->Sound and experiment changing drivers in there using the test sounds. You should be looking at the options concerning playback. Default mixer in the bottom option may have changed.

I mention these because something changed on my computer one day an it had changed a driver for some reason but everything has worked fine since I changed it back.

Good luck and let us know ... :)

---

### Post by Dark006 on 2008-08-09
Thank you both! I guess my sound was muted lol.

---

### Post by Bucky Ball on 2008-08-09
Glad to help, easy mistake. Done that more times than I care to remember, which is why I suggested as did st33med before me I notice ... :)  lol

---

