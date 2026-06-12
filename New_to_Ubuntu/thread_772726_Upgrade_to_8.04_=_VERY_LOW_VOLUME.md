---
title: "Upgrade to 8.04 = VERY LOW VOLUME"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Own3d on 2008-04-28
After recently upgrading to V8.04 from 7.10 of ubuntu my volume will only play at an exceptionally low level of loudness , And thats with all the volume levels turned up , ( The one by the date ) ( The One on the mediaplayer ) etc ALL turned up to highest settings and still only a tiny amount of sound.

---

### Post by dearingj on 2008-04-28
Have you tried this?

Right-click on the volume icon (the one by the date) and choose "Open volume control"
Turn up the volume controls in the window that appears

---

### Post by Yadda on 2008-04-28
I, also, am experiencing this problem. I tried this: "Right-click on the volume icon (the one by the date) and choose "Open volume control" Turn up the volume controls in the window that appears"
It helped slightly but the volume still goes mute when the bar is only half way down. I have also tried setting everything to use ASLA rather than pulse audio... no dice. My sound card is an Intel 82801G (IH7 Family) High Definition Audio Controller.

---

### Post by TeoBigusGeekus on 2008-04-28
If you use alsa, type

```
alsamixer
```

in a terminal and adjust master volume from there.

---

### Post by Yadda on 2008-04-28
Thanks for the reply, no luck with alsamixer either. I've got everything that been mentioned or that I can find maxed out and am still experiencing the problem.

---

### Post by andylyon11 on 2008-04-29
I also have this strange problem. Sound IS working but is much quieter in this new version. Anyone have ideas?
Thanks

---

