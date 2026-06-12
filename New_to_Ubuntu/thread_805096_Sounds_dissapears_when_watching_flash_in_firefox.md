---
title: "Sounds dissapears when watching flash in firefox"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by Kuraboy on 2008-05-23
Hi!

I have a problem, sometimes when I am washing flash clips on youtube in Firefox 2 the sound just wont work anymore, and in the console I get this error:

"ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave"

The only way I know how to solve it is restart Kubuntu (7.10).

Thank you in advance

---

### Post by alienexplorers on 2008-05-24
have you tried resetting ALSA with this command:
> sudo /etc/init.d/alsa-utils reset

---

### Post by Kuraboy on 2008-05-25
Hi, 

I have tried it before but it didn't help, I don't have sound in the whole system.

---

### Post by markbuntu on 2008-05-25
Have you tried setting everything in System/Preferences/Sound to alsa instead of automatic?

---

