---
title: "Cheese not running in 12.04 - segmentation fault error"
date: 2013-06-12
forum: New to Ubuntu
---

### Post by Zornicator on 2013-06-12
Hi All,

I'd sure like to use Cheese. My webcam works fine (VLC has no problem with it). I'm using 12.04. Running ```
cheese
``` from the terminal I get the following:

```
Xlib:  extension "GLX" missing on display ":0".
Segmentation fault (core dumped)
```

If I try to run it from the desktop then the icon pops up but nothing happens.

Thanks!

---

### Post by Isamu715 on 2013-06-15
Are you using an nVidia card? Which driver is currently in use on your system?

---

### Post by Zornicator on 2013-06-18
My graphics card is an NVIDIA Quadro K1000M. How do I determine which driver is in use? Thanks for your post!

---

### Post by Isamu715 on 2013-06-24
If you didn't install any drivers yourself then you're running the stock open-source Nuevau driver. Try installing the official nVidia driver from the "Additional Drivers" utility.

---

