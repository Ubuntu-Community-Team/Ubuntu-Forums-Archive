---
title: "Ripping audio from video?"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by MrPatton84 on 2008-11-13
Hey everybody, 

Is it possible to rip audio from a video - more specifically a wmv file? 

Thanks in advance, 

Chris

---

### Post by LowSky on 2008-11-13
you need mplayer to do what I'm suggesting, so install that first

then follow the instructions here, its all command based but i will work
[http://linux.byexamples.com/archives/229/extract-audio-from-video-or-online-stream/](http://linux.byexamples.com/archives/229/extract-audio-from-video-or-online-stream/)

---

### Post by JunCTionS on 2008-12-20
thanks!
although byexamples.com seems to be down, I had to read it through the google cache.
basically this is the line that helped me:
> ffmpeg -i nodame_theme.flv -ab 128 -ar 44100 nodame_theme.mp3

-i is to specified input file, -ab audio bitrate, -ar audio sampling frequency

Although ffmpeg corrected me and pointed out that the bitrate is expressed in bits and not kbits so for me it was really:
```
ffmpeg -i video.ogg -ab 128000 -ar 44100 audio.mp3

```

---

