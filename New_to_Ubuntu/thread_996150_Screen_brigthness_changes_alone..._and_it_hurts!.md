---
title: "Screen brigthness changes alone... and it hurts!"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by arashiko28 on 2008-11-28
I want my screen brightness to be and stay as I put it, but when I'm reading and take a while to act, the screen changes suddenly to the brightest and causes me pain in my eyes. I thought that I would tolerate this, but it's getting me on my nerve, I suffer from migraine and have found this as a trigger for my episodes.

I saw the option of making the screen dim when idle, but it does all the contrary, even if that option is not marked.:confused:

---

### Post by cwsnyder on 2008-11-28
Sounds like either a video driver problem or a monitor problem.  My screen gradually goes **dark** if I don't either type or move the mouse within about 15 minutes.

---

### Post by arashiko28 on 2008-11-28
Mine takes 5 or less. I have no other video issues, so I can't relate it. The computer is brand new and don't do this in windows.
BTW, the video is intel...

---

### Post by a0u on 2008-11-28
See if the problem can't be solved by setting the backlight level manually.  I notice that xbacklight sometimes keeps the backlight more constant than the brightness applet does, for some reason.

```
sudo aptitude install xbacklight
```

In the terminal:
```
xbacklight -set <percentage>
```

---

