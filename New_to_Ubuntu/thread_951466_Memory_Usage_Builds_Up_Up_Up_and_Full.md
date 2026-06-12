---
title: "Memory Usage Builds Up Up Up and Full"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by subzero316 on 2008-10-18
I have 1 gb of memory. Over the time the Usage fills up. For instance I turn on and watch a dvd(What I usually do) by the time the movie gets over the memory is full around 950mb is occupied though swap is free 100%. This happens all the time :confused: Not just with movies but If i just leave it On for a looooong time it fills up. I use VLC to watch dvds. Why does this happen it becomes sluggish once its full(when I then load other programs) then starts eating swap - reading my hard disk constantly(swapping I guess) .??? .. Is there a cure I hate the constant grinding of my hardisk when all I do is watch a movie or browse.

---

### Post by Hossie on 2008-10-18
Look at free -m (the line with +/- buffers). Thats the "real" mem usage. Intelligent operating systems use free memory as buffers.

---

