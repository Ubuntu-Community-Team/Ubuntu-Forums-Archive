---
title: "Games flashing"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Sheneron on 2008-04-26
Whenever I play a game such as tuxcart, or neverball, the screen flashes every few seconds.  Does anyone know what could be causing this and how to fix it?  Thanks

---

### Post by Google Spider on 2008-04-26
> **Sheneron said:**
> Whenever I play a game such as tuxcart, or neverball, the screen flashes every few seconds.  Does anyone know what could be causing this and how to fix it?  Thanks

Is graphics driver enabled?

If not go to **System>Administrator>Hardware Drivers** and enable it.

---

### Post by Sheneron on 2008-04-27
Yep it is.

---

### Post by kavon89 on 2008-04-27
> **Sheneron said:**
> Yep it is.

Well, lets see if the 3D is working...

```
glxgears
```

Let it run for about 10 seconds, post the results. (the frames per second)

---

### Post by Sheneron on 2008-04-27
4894 frames in 5.0 seconds = 978.704 FPS
5478 frames in 5.0 seconds = 1095.550 FPS

---

### Post by Helios1276 on 2008-04-27
Try turning off compiz effects for a sec, I personally cant run both at the same time

---

### Post by Sheneron on 2008-04-27
That seems to have done it.  Thanks

---

### Post by Helios1276 on 2008-04-27
you can set profiles in compiz manager to make it easier to switch back and forth too

---

### Post by Sheneron on 2008-04-27
I am glad I check this again because I just lost the settings.  Thanks.

---

### Post by garbergs on 2008-04-27
Just in case someone else is as clueless as I am:

System -> Settings -> Appearance -> Visual effects -> Select "None".

I'm on a fresh installation of Ubuntu 8.04 desktop.

---

