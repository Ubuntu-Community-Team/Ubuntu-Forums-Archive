---
title: "no sound in vlc"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by Faud on 2008-05-03
Hi guys, Upgraded to 8.04. Seems everything is fine. I have sound in other applications, however I dont have any sound on VLC player when watching a video.
Any ideas ?

---

### Post by macaholic on 2008-05-03
Have you tried fiddling around with the various output devices in the VLC preferences?

---

### Post by riven0 on 2008-05-03
Also, PusleAudio may be giving problems. It happened to me, but disabling PusleAudio and restarting Alsa seemed to have fixed the sound issues. 

I also noticed a weird bug; whenever the sound goes out, playing an .ogg file will bring it back. Strange, but it worked for me.

---

### Post by spudratic on 2008-05-03
first right click the volume icon open the volume control edit preferences and check what you need and make sure the levels are up,then open vlc,settings preferences check advanced options go to the audio triangle and expand highlite output module and select pulse audio.save exit restart player.see if this helps you can also install alsa on hardy thought I book marked a guide for alsa in hardy guess not search I found it so I know you can.you guys are fast lol

---

### Post by Faud on 2008-05-03
Many thanks guys.

---

### Post by spudratic on 2008-05-03
If your using pulse audio only put the pcm volume half way to start in the volume control.If the pcm setting is to high it makes all sorts of distortion.

---

