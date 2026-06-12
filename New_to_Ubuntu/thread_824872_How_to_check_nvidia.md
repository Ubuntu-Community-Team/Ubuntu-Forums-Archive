---
title: "How to check nvidia"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Rocco82 on 2008-06-10
Hi there, anyway I can check if my nvidia card is working properly?

Got the resolution back after (finally) a succesfull install. but dont see any option for the card. want to check the if 3d accel. and open gl is working properly.

got a nvidia8400 gs

thanks, rocco

---

### Post by wolfen69 on 2008-06-10
the best way to check it would be to install an app that is dependant on 3D, such as a game or app such as Google Earth.

---

### Post by lswest on 2008-06-10
best tests:
```
glxinfo|grep direct (should return "direct rending: yes")
glxgears (framerate should be about 2000 on most cards, probably well about 4000 for you)
``` and doing ```
cat /etc/X11/Xorg.conf|grep nvidia
``` and if that returns something the driver is in use.

---

### Post by okey666 on 2008-06-10
Does Compiz work well. And do the 3D screen savers perform upo to speed. That should give you an idea.

---

### Post by wolfen69 on 2008-06-10
> **lswest said:**
> best tests:
```
glxinfo|grep direct (should return "direct rending: yes")
glxgears (framerate should be about 2000 on most cards, probably well about 4000 for you)
``` and doing ```
cat /etc/X11/Xorg.conf|grep nvidia
``` and if that returns something the driver is in use.

those things may indicate that things should work well, but a "real world" test is the best option. if a 3D game or app works well, you are set.

---

### Post by lswest on 2008-06-11
> **wolfen69 said:**
> those things may indicate that things should work well, but a "real world" test is the best option. if a 3D game or app works well, you are set.

Sure, I just meant "best" as in you wouldn't have to install any software to test it.  I tend to avoid any games on my laptop, so I wouldn't install any to check the drivers of my graphics card.  Of course, that is a valid test.  Also, you had already suggested it, so I wouldn't have had to mention it again, just added to your idea.

---

