---
title: "Pulse audio starts crackling after a while"
date: 2012-05-28
forum: New to Ubuntu
---

### Post by venom104 on 2012-05-28
I switched from oss4 to alsa + pulseaudio (actually I used the esound package)...anyway, I have a small problem where after a while a while my audio starts crackling after a while; killing and restarting the pulseaudio deamon seems to fix this, but I kinda don't want to have to restart all the programs I have running just to get my sound back.

I do not want to switch back to OSS4, but what can I do to get this working? 

Here is my hardware

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1400129&CatId=4928](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1400129&CatId=4928)

---

### Post by venom104 on 2012-05-30
I FOUND A FIX!...open up a terminal and type rm -r ~/.pulse ~/.asound* ~/.pulse-cookie . I put this in my .profile file, and I haven't had any problems since.

I am guessing that pulseaudio is picking up some funk settings from a global configuration file...anyone know what that file would be?

---

### Post by Hadaka on 2012-05-31
This is a pretty good overview of pulseaudio and how it works.
[http://en.wikipedia.org/wiki/PulseAudio](http://en.wikipedia.org/wiki/PulseAudio)

If you are running Alsa..you really dont need it. it can be removed
from your system...but you do lose the volume slider control under
the speaker icon. I cant seem to locate the link for removing it, but
if you are interested as to how....i can dig a little and locate it.

---

### Post by brainwash on 2012-05-31
> **venom104 said:**
> I am guessing that pulseaudio is picking up some funk settings from a global configuration file...anyone know what that file would be?

Doesn't PA recreate the .pulse folder and .pulse-cookie file anyway if they are missing? Not sure, if all your applications are affected by the mentioned audio crackling, but I noticed the same behavior while testing Diablo 3 (wine) on one of machines (actually my only system running PA). Due to lack of time I was not able yet to find the cause the sound malfunction.

You might want to check the content of /etc/pulse/default.pa and maybe adjust some of the default values.

---

