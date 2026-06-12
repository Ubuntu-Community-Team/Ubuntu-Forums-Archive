---
title: "troubleshoot help - Hardy occassional unresponsive black screen"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by getut on 2008-11-12
I'm having trouble with a Hardy 32bit desktop PC that is fully up to date.

Occasionally, once every other day or so, it will seem to be frozen and go to a black screen. It will not respond to any keyboard commands, won't switch to a terminal with CTRL-ALT-F2 or such. It can be pinged and can be SSH'd into and rebooted normally and then it comes back and works fine until next time. It goes into this state sometimes while using it, other times while sitting idle.

Any idea how to troubleshoot this issue?

---

### Post by stephanvaningen on 2008-11-12
I have had a similar issue, it has disappeared now and I figure it had something to do with my ATI video-card: what's your card?

---

### Post by getut on 2008-11-12
Mine also is an ATI Video card. Since my original post I found some interesting xorg log entries that gave me something to search on and I think I have found a bug report that someone else entered that closely matches the issue I am having.

My Xorg.0.log goes into a loop of the following 2 lines of error message over and over when it gets into that state:

mieqEnequeue: out-of-order valuator event; dropping
tossed event which came in late

Googling the error turns up quite a few hits in many distributions of linux with many different video cards.

I found the bug related to many xorg issues, but after reading all the way through them, it seems it is actually a kernel issue with the kernel not sending proper release events. So it looks like I will just have to wait because the latest kernel in proposed still didn't fix it for me.. it just made it a little less frequent.

---

