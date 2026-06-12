---
title: "Freezing up"
date: 2014-05-07
forum: New to Ubuntu
---

### Post by yayzooty on 2014-05-07
Hey, I recently installed xubuntu and I have quite a large problem.

Whenever I press printscreen, try to lock the screen or attempting to make a screenshot my desktop freezes up and it's like an animation that plays at thirty frames per minute. I can go into a tty session and type service lightdm restart and that fixes it, but it is very annoying.

Can anyone suggest any fixes?


Edit: I read online that I should switch to proprietary drivers and run a software update, now it doesn't start. At the end of /var/log/Xorg.0.log I see 
segmentation fault at address 0x10 
Caught signal 11. Server aborting

Edit 2: I started xubuntu with "nomodeset nosplash verbose", from there I was able to set my graphics drivers back to the default and that also fixed my original problem.

Sorry for the bad formatting, I'm writing this on a phone now.

---

