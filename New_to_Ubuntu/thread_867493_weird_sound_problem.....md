---
title: "weird sound problem...."
date: 2008-07-22
forum: New to Ubuntu
---

### Post by Tibco on 2008-07-22
Hi, i have a weird sound problem here. When i go to system>prefrences>sounds and adjust all my playback options to "C-Media PCI DAC/ADC" instead of auto detect, i can play sounds ONLY with totem movie player. I dont get the login screen tone, i also CAN'T play sounds with (s)mplayer or vlc, which is really weird!! Like i said, i cant hear any system sounds like login or stuff, unless it is specifically opened with Totem video player. Does anyone have any clue? Also i would post my sound card if i knew how i could find out...

EDIT: If i leave my sound option to auto detect, i cant play sounds with ANYTHING including totem...

---

### Post by Tibco on 2008-07-23
bump. if any one is confused as to what im asking, go ahead and ask.

---

### Post by northern lights on 2008-07-23
Can you post the output of ```
cat /proc/asound/cards
```

---

