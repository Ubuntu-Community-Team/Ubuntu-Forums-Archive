---
title: "Monitor resolution not changing"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by gnite on 2013-07-19
Hi, I have been scouring the web for answers and know there have been lots of questions regarding resolutions, but none that would answer my particular problem, or at least none that I could find. I am running a live CD of Ubuntu 13.04 64bit since I am not yet committed to actually installing it, as this one is a pretty big issue for me.

When I start the system it sets a default screen resolution of 1280x1024, I then go into system settings and change it to 1600x1200 which is the one I always use on my 21" CRT monitor. It does change the resolution of what Ubuntu is rendering, making a screenshot and looking at it in Windows gives me a perfectly sharp image that's 1600x1200 in size, but in Ubuntu it looks awful, blurry, pixelated. As far as I can tell, the monitor is still displaying at 1280x1024. Just to test this, I changed the resolution to 800x600 and yeah, the image then looked amazingly sharp for such a low resolution.

One thing I tried to fix it was restarting the X server using either *sudo restart lightdm* or ctrl+alt+backspace (if I remember correctly), but restarting it did nothing to help. I'm really hoping to find a solution, this is the one thing that is keeping me from going the GNU/Linux way.

---

### Post by dino99 on 2013-07-19
1 thing i would like to know:

- which graphic card is it ?

---

### Post by gnite on 2013-07-19
It's a nvidia 8800 GTS 512.

---

