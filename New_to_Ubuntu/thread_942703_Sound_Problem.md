---
title: "Sound Problem"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by ealrgrey on 2008-10-09
Hi everyone!

I'm using Ubuntu 8 on my laptop. When I use Firefox to watch Youtube videos etc the sound is fine, and when I use Rhythmbox the sound is fine. But if I'm listening to Rhythmbox and then go to Youtube, I cannot get any sound from Youtube when Rhythmbox is running, and even if I close Rhythmbox at that point sound will not return to Firefox until I restart Firefox with Rhythmbox not playing. Any ideas why that is happening? When I had Vista on this laptop the sound was fine.

Thanks very much!!

---

### Post by Legend28469 on 2008-10-09
are you using hardy heron... or intrepid ibex...

(KEEP IN MIND).. intrepid ibex is still in development

---

### Post by ealrgrey on 2008-10-09
Hi! I'm using Hardy Heron :)

---

### Post by ealrgrey on 2008-10-09
BUmp!

---

### Post by blazemore on 2008-10-09
I've had this issue.
It's to do with Pulse Audio.
There's two things I did to fix it:

1) In System->Preferences->Sound, change all output devices to the relevent ALSA (Not Pulse)
2) Search Gstreamer in Synaptic and install ALL Gstreamer plugins, no matter how small or trivial.

---

