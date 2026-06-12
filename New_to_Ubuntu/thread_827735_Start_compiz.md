---
title: "Start compiz"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by danielrs on 2008-06-13
When I try to enable compiz: system-preferences-appearence-visual effects, I get the error: "The composite extension is not available", I've have checked synaptic and compiz is installed...

---

### Post by joshsmith on 2008-06-13
if you dont have an nvidia, ati, or intel graphics card you are going to be out of luck with compiz

if you have nvidia or ati, look in system>admin>restricted drivers
intel have open source drivers so they just work

---

### Post by alienexplorers on 2008-06-13
Do you have the correct version of your video driver installed and running.  Try running glxgears from terminal to see if your drivers are working up to par.  A number over 1000 is pretty good at least for my system.

---

### Post by Victormd on 2008-06-14
> **alienexplorers said:**
> Do you have the correct version of your video driver installed and running.  Try running glxgears from terminal to see if your drivers are working up to par.  A number over 1000 is pretty good at least for my system.

A number over 1000 for what parameter?
I have a pretty good graphics card (see my signature) and this is what I get:
> 303 frames in 5.0 seconds = 60.402 FPS
300 frames in 5.0 seconds = 59.886 FPS
300 frames in 5.0 seconds = 59.886 FPS
300 frames in 5.0 seconds = 59.886 FPS
300 frames in 5.0 seconds = 59.887 FPS
300 frames in 5.0 seconds = 59.886 FPS
300 frames in 5.0 seconds = 59.885 FPS


Not even close to 1000... Any thoughts?

---

### Post by RomeReactor on 2008-06-14
Hi. How long have had your Ubuntu system installed? Which version is it? Please run this command from the terminal (Applications->Accessories->Terminal):
```
glxinfo | grep rendering
```

If the output is 'Yes', then the problem may be if you have an integrated VIA gpu in your motherboard.

---

### Post by Rocket2DMn on 2008-06-14
Can you please post your video card make/model for us by running
```
lspci | grep VGA
```

---

