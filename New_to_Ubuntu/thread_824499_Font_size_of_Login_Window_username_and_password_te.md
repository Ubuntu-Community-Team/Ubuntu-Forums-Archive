---
title: "Font size of Login Window username and password text is very big"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Guruprasad on 2008-06-10
Username and password text on login page is very big.

How to reduce it?

---

### Post by neksys on 2008-06-10
Its an easy fix. System > Administration > Login Window

Go to Security. Click "COnfigure X Server"

Add "-dpi 96" (without the quotes) to the end of the Command box.

---

### Post by frup on 2008-06-10
With out more information I can give you some simple things to try. I am no expert.

1) Try having your screen on when you turn on your computer (or off) For me, if the screen is off when x initialises the screen resolution/monitor detection sometimes doesn't work properly. This is a result of xorg 7.3 I believe and may not actually be an issue any more as I have been using 8.04 since beta and haven't paid attention to the problem since. I'm guessing your problem is most likely to be in the realm of screen resolution.

2) You could try a different GDM theme. One which is more minimal

I had more ideas when I began writing this but it's late at night here and I'm not thinking 100%.

---

### Post by Guruprasad on 2008-06-12
> **neksys said:**
> Its an easy fix. System > Administration > Login Window

Go to Security. Click "COnfigure X Server"

Add "-dpi 96" (without the quotes) to the end of the Command box.
HI

I tried making changes but something went wrong... I think I entered the text wrongly... Now my Xserver crashes within few seconds of starting...

Can please tell me where is the file which saves these settings so that I can edit it without starting GDM?

---

