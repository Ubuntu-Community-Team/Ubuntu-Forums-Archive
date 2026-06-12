---
title: "no sound, sometimes?"
date: 2012-08-09
forum: New to Ubuntu
---

### Post by pcircle85 on 2012-08-09
Hello, completely new to Ubuntu and Linux and I'm having issues with my sound.

I've done everything detailed here: [http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/](http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/)

I've installed the codecs package.

I've installed pulse audio controls.

And yes, I've made sure it's not muted anywhere. 

But, sound -does- work -sometimes-. Logging in/logging out plays a sound, the sounds available in the sound settings play. The issue is mainly with Empathy. No sound at all. I downloaded Pidgin sounds, thinking the Empathy sounds were just too soft or something, but even those make no sound, but not just through Empathy, simply trying to play the .wav or .ogg produces no sound.

Thanks in advance. 

-Nick

---

### Post by marlow59 on 2012-08-09
Try to type this into a terminal : 
 :~$ killall pulseaudio
 :~$ pulseaudio

---

### Post by pcircle85 on 2012-08-09
> **marlow59 said:**
> Try to type this into a terminal : 
 :~$ killall pulseaudio
 :~$ pulseaudio

No luck.

Also, I've no sound from Youtube or any other sound-making source...

---

