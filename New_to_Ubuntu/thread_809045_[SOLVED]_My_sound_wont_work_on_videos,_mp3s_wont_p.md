---
title: "[SOLVED] My sound wont work on videos, mp3s wont play, why is this happening?"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Bob_12 on 2008-05-27
VLC is completely silent, as well as Mplayer for all types of video, including DVDs, and all types of sound files, Amarok and Rythmbox wont even play mp3s, but for some reason flash videos online have sound. What can I do to fix this? I'm dying without my muisc! Thanks!

P.S. I have all the restricted extras installed.

---

### Post by Bob_12 on 2008-05-27
I just fixed it by turning off the visualizations in Hardy....why did this fix it and is there any way I can get my pretty OS back and keep the sound?

---

### Post by billgoldberg on 2008-05-27
> **Bob_12 said:**
> I just fixed it by turning off the visualizations in Hardy....why did this fix it and is there any way I can get my pretty OS back and keep the sound?

I believe you experienced the pulseaudio + flash bug.

If you have at any time a flash application open, then you won't get sound from other applications.

Or if you have a song or movie running, you won't get sound from flash videos.

The solution is pretty simple and you don't need to turn of visualizations.

You can either do this command (not advised)

```
sudo apt-get install libflashsupport
```

*(this will fix the problem but could make flash a bit unstable)*

or you could use Alsa instead of PulseAudio.

[link]("http://linuxowns.wordpress.com/2008/05/07/hardy-sound-problems-2/")

---

### Post by Bob_12 on 2008-07-03
Thank you so much!

---

