---
title: "Java Frame background import help"
date: 2009-01-05
forum: Programming Talk
---

### Post by nightflre on 2009-01-05
...

---

### Post by Zugzwang on 2009-01-06
> **nightflre said:**
> Hi guys, i need help with importing images into a Frame. I got it to work, but the background picture(mypic.gif)is never beneath the animation. So my question is: how can i alter the code so that it does go beneath everything? Btw, just have a picture named mypic.gif in the same directory as the program


Why do you paint the background in the update()-method but the rest in the paint()-method? Just make sure that you draw the background image into your offscreen buffer before you put anything else into it, remove the drawing command from the update-method and you should be fine. Haven't tried your program, tough.

---

