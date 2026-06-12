---
title: "&quot;Rapid&quot; audio playback"
date: 2009-09-08
forum: Programming Talk
---

### Post by Hexorg on 2009-09-08
Good daytime everyone! I'm trying to write a little drum machine programm, so I need to play simple wav file under linux (alsa), however
- I need to have the minimal delay between the condition to play sound is true(hit of a drumstick), and sound is output to speakers
- I'll have to play second sound before first one is over ("Rapid")
- And it'd be nice to be able set the gain of the output sound.

What library to use would be the best (I'm very new to linux multimedia programming)?
I found little sourse of a simple playback using libasound(alsa lib), but that was made to play raw audio, not wav. And system("aplay %s") can't really play sounds that fast and always waits untill the file playback is over.

---

### Post by Hexorg on 2009-09-09
Or is there any system funcltions to play audio?

---

### Post by haTem on 2009-09-09
Have you tried gstreamer? I believe it can accomplish what you're after. (there's also phonon, if you're using Qt for your UI)

---

### Post by Hexorg on 2009-09-09
I don't have UI, it's going to work in the background. I'll see what I can get with gstreamer :)

---

