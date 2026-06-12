---
title: "[Python/Pygtk]How to set image as background in window"
date: 2011-06-26
forum: Programming Talk
---

### Post by Dhiraj Thakur(Invincible) on 2011-06-26
hi all, i wanted to set an image in the background of a window how can i do that .... i hv already gone through pygtk docs and the code they have hangs after some time...i wanted to know is thre any other way i can do that....plzzz show me with code ... if u can..pllzz help.... :)

---

### Post by Arndt on 2011-06-26
> **Dhiraj Thakur(Invincible) said:**
> hi all, i wanted to set an image in the background of a window how can i do that .... i hv already gone through pygtk docs and the code they have hangs after some time...i wanted to know is thre any other way i can do that....plzzz show me with code ... if u can..pllzz help.... :)

I keep the bitmap as an attribute of my window class, and use dc.DrawBitmap in my OnPaint method.

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-28
Thanks fr help arndt :)

---

