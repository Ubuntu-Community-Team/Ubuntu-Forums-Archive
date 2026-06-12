---
title: "Help with boot screen"
date: 2016-03-14
forum: New to Ubuntu
---

### Post by olegklyuchak on 2016-03-14
So after finally getting ubuntu running do to issues with my "fake" raid array, I've run into a little problem.

I installed the drivers for my new Nvidia GTX 970, and after doing so my splash screen at boot went to 640x480. I also had the issue that I was stuck in a loop at the login screen.

To fix that I got the "boot repair" utility and after running that, I was able to login again. But now, instead of seing the boot animation (plymouth), I was seeing a verbose boot, still at 640x480.

After scouring the Internet for solutions and trying everything I can, I've only been able to get it to the native resolution, but I still see the verbose boot instead of plymouth (pictured)

I've tried re-installing and editing plymouth, along with countless other things that I can't even remember at this point, but I still find myself scratching my head. Anyone got any ideas how I can get the animation back?


EDIT: I got it working by changing the GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub and adding quiet & splash.

[IMG]http://i.imgur.com/HYrX0LRh.jpg[/IMG]

---

### Post by Edison_James on 2016-03-15
Welcome to the forum, Glad it worked out for you.

---

