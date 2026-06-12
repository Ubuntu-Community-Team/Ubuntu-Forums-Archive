---
title: "Stumped by Skype"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by intoutdoor on 2012-11-18
Hello,

   I just installed 12.04 and could not seem to find skype anywhere in the software center.  I went to skype's site, downloaded it from there (of course opened with the ubuntu software center) and now skype opens, and can make calls, but no audio works (despite working on youbube and rhythm box).  I ran a command to check to see if my drivers for my sound card are in order, and it appears that they are.  The strangest thing yet, is that when I go to "installed" in the software center, Skype is no where to be found, despite it obviously being on my machine.  

If any advice would be greatly appreciated.

Best

mack

---

### Post by monkeybrain2012 on 2012-11-18
Skype is in the Canonical's partners repository, it is not enabled by default, you have to check a box in the Software Centre to enable it (just poke around to find it, since I don't use the SC I don't know where it is, I use synaptic, in synaptic you go to Settings > Repositories > Other Software to check the box)

For the audio, install gnome alsa mixer from the Software Centre and try with the settings, you probably have capture muted or something.

---

### Post by intoutdoor on 2012-11-18
Thank you,

I checked that box, but still no dice.

I will give the audio idea a shot. Thank you!

---

### Post by intoutdoor on 2012-11-19
It was the Alsa mixer. Thank you!

---

