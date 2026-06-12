---
title: "[SOLVED] No sound in Flash, VLC, others..., starting just yesterday?"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by diablo75 on 2008-05-27
Well, VLC wasn't playing audio, but I managed to get it fixed by telling the output modual to use Pulse Audio instead of ALSA.  ALSA, up until yesterday (apparently) was working just fine for me with VLC, but not anymore.  I was using it because Pulse Audio isn't quite glitch free yet.

Flash doesn't work anymore, and probably for a similar reason.  Where do I go to check flash audio settings and see where the output sound is being directed?

---

### Post by abadam5167 on 2008-05-27
[http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)
Do everything that is given in that link and you can get the best out of Pulse Audio. If you do not need audio editing or video editing tools, just uninstall Pulse Audio. It is not widely supported yet. Skype will not work unless you select raw device handling and suspend pulseaudio for the time when u want to use skype. There are a ton of other unsupported apps.

---

### Post by diablo75 on 2008-05-27
> **abadam5167 said:**
> [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)
Do everything that is given in that link and you can get the best out of Pulse Audio.

No thanks.  That's not something I feel like wasting hours of my day on.  It'd be easier and less time consuming to backup my home folder and do a destructive recovery.

---

### Post by diablo75 on 2008-05-28
Just wanted to let everybody know my problem was solved by installing the "libflashsupport" package using Synaptic Package Manager.  Why this wasn't suggested by anybody earlier... :confused:

---

