---
title: "[SOLVED] screensaver problem-screensaver starts but will not stay activated"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by huntwell on 2008-08-28
I am having a strange problem with the screensaver. I have set it to the blank screen and when it activates, it comes back out of screensaver mode almost immediately afterward. I think there may be a program running that is causing the problem, but not sure which. It happens over and over if left to go in screensaver mode. I can restart my computer and it doesn't happen right away, but eventually if the computer is left long enough, it happens.

Any help with this issue would be greatly appreciated. Thanks in advance.

---

### Post by alienexplorers on 2008-08-28
Did you happen to notice if it is happening to just certain screensavers such as those requireing open-gl.

---

### Post by huntwell on 2008-08-28
> **alienexplorers said:**
> Did you happen to notice if it is happening to just certain screensavers such as those requireing open-gl.

Thanks for the quick reply. I tried several screensavers and the same thing happened, as soon as it phased into the screensaver, it came back out.

I have both compiz-fusion and cairo-dock installed and when I used compiz-switch and closed cairo-dock, the screensaver activated and stayed in screensaver mode, but when I tried to get the screen out of screensaver mode by moving the mouse, it froze and I had to do a hard restart.

I also tried only stopping compiz-fusion, and the screensaver would activate and stay in screensaver mode, but it went into a blank screen no matter what screensaver I chose.

I then tried leaving cairo-dock and stopping compiz-fusion, and it would go into screensaver mode and actually show the screensaver chosen, such as AntInspect, but when I tried to get it to come out of screensaver mode, it would freeze and I had to do a hard restart. 

I am assuming then that it has something to do with either cairo-dock, compiz-fusion, or both.

What are your thoughts on this issue? Thank you again.

---

### Post by huntwell on 2008-09-07
Apparently, it has something to do with Cairo-Dock. When I take it out of the startup menu to start automatically, it solves the problem.

---

