---
title: "Audacity Multi-Track Problems"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by stoogiebuncho on 2008-06-01
I've been using Audacity since well before I decided to switch over to Ubuntu, and I never seemed to have any trouble with it in Window$, but in Ubuntu it has been giving me trouble.

First was the problem of being able to hear play-back while you are recording a new track.  Some time spent on Google was able to help solve that problem.

Now I've upgraded to Ubuntu 8.04 and it's not working again.  It records a single track just fine, but if you want to record an additional track, it creates the new track but freezes up, and doesn't play or record anything.  The record button stays in the depressed position, but the 'cursor' thing doesn't move at all, it just flickers in place.

I've heard running the windows version under WINE sometimes works better, but it seems like there should be a better solution than that.  Anybody have any bright ideas?

---

### Post by Wandering on 2008-06-01
I don't know what will work for you, but for me, I found I had to kill pulse audio processes before I start Audacity. Then it seems to work about as well as under Vista. When I have finished with Audacity, I just reboot to restore my sound to normal. 

Maybe it will work for your.  Good luck.

---

### Post by ibuclaw on 2008-06-01
Go into "**System>Preferences>Sound**" in the Gnome Menu and change all sound playback from "**PulseAudio**" to "**ALSA**".

Regards
Iain

---

### Post by markbuntu on 2008-06-01
Audacity uses jack for sound and doesn't always close jack when it is finished. It also will not let go of alsa. You can fix some of this if you have jackcontrol which is in the repos. You can set the input and output to alsa and you can kill jack from jackcontrol when you are finshed with it. You can also use jackcontrol to use your sound card directly in the input and output and set it to realtime to reduce latency for recording amd mixing and adjust the buffers to get rid of xrun errors.

---

### Post by stoogiebuncho on 2008-06-01
Thanks for the tips, I had already set it all up to go through ALSA, which is what fixed the problem for me the first time.

This time it's different in that it doesn't give me any sort of error message, it just opens a new track, and everything freezes up until you press the stop button.  

I might play around with that jackcontrol thing a little and see if anything comes of that.

---

