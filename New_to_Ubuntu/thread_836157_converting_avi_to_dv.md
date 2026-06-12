---
title: "converting avi to dv"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Nolander on 2008-06-21
Ive tried,
```
ffmpeg -i some.avi -target ntsc-dv some.dv
```

But it give me,
```
[dvvideo @ 0x2b2608414e50]Can't process DV frame #1. Insufficient audio data or severe sync problem.
```

over and over, the same frame 20 times, for 20 frames. and then the new file is zer0 seconds.

~nolander

---

### Post by bumanie on 2008-06-21
Try the program devede, available from the repo's. > sudo apt-get install devede

---

### Post by Hospadar on 2008-06-21
devede is really nice and easy, if it doesn't work for you though, give avidemux a shot, there's a helpful wiki on their website and they have some good auto options for outputs

---

