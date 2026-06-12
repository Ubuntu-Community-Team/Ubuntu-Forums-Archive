---
title: "Problems with flash audio"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Morpheun on 2008-06-09
I have ubuntu restricted extras installed to play some of my media files (mainly avis and mp3s) however, it seems to be messing with flash playback (with adobes official player, but gnash and the other's don't work either)  when I start youtube and the likes it will play audio, but only if I haven't played any music or watched any videos yet. Conversely if I have already watched youtube videos playing music or watching movies won't produce any sound. As of now it really leaves me choosing between the two which is not a situation I want to be in and I need some way to fix this.

---

### Post by isaacj87 on 2008-06-09
Open up terminal and try this:

```
sudo apt-get install libflashsupport
```

Restart your browser and see if that helps any. It could potentially make firefox crash a lot more often. But, unfortunately, at this point it's like a pick your poison situation.

---

### Post by powerpleb on 2008-06-09
I had the same problem so I followed this guide to setup PulseAudio:
[http://ubuntuforums.org/showthread.php?t=776739&highlight=pulseaudio](http://ubuntuforums.org/showthread.php?t=776739&highlight=pulseaudio)

And everything worked well for me. Now I can watch flash with audio, play games and play mp3s at the same time.

---

### Post by Morpheun on 2008-06-09
libflash didn't work, thanks for the help though, any other suggestions?. Btw, I don't know if this is related, but playing the actual flv files works fine, if I can get the direct link to the video.

---

### Post by Morpheun on 2008-06-09
Hmmm... It seems to have magically fixed itself, I went to try the pulseaudio method so I reinstalled the nonfree flash and it just sorta worked. Right now I have this horribly distracting mix of two songs blaring in the background :-D. Thanks for the help everyone.

---

