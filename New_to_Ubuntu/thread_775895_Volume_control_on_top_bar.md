---
title: "Volume control on top bar"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by pzs on 2008-04-30
I'm on Hardy Heron - I can't remember if it worked properly before. It goes up and down but the volume I can hear (of a YouTube clip or mp3) remains the same, even if I set the volume control to mute. 

I presume this means that it's not connected to the right audio source, but I've tried the various devices and tracks listed in preferences (Alsa mixer, some "capture" and "playback" sources) and it doesn't seem to make any difference.

---

### Post by zvacet on 2008-04-30
Apps>sound & video>volume controle>file (here you can select ALSA or OSS)>edit>preferences(or settings)>be sure that you have MASTER and PCM enabled.You can addsome more but these two you must have.

---

### Post by cornelis spronk on 2008-04-30
I tried zvacets reply and it does not work.  However it got me to try a left clickt on the double speaker, and I selected the card in my computer, and it has made it made the volume control pop-up bar work.  Thanks for the suggestion, even though I think it was made from inaccurate memory.

---

### Post by forrestcupp on 2008-04-30
I think it has to do with the new Pulse Audio.  I just went to System->Preferences->Sound and set everything to ALSA.  If you do that, the volume slider will work with YouTube videos.

Before you do that, make sure you don't need the supposed benefits of Pulse Audio.

---

