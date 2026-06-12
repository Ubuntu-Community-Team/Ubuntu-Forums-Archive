---
title: "I am getting flickering/tearing at login screen on wake up...anyway to fix this?"
date: 2020-08-08
forum: New to Ubuntu
---

### Post by automate-stuff on 2020-08-08
I am getting some flickering(or should i say tearing?)  when waking up...is there a way to fix it or is it how it is supposed to be: 


[https://youtu.be/T1wvXLaZh3A](https://youtu.be/T1wvXLaZh3A) 

sometimes it is worse than the video...sometimes the flickering/tearing happens to the desktop too when the desktop appears for the first time after login.
This doesn't happen when I wake-up/swipe/suspend/wakeup again ... there is no swipe screen in this case...any way to disable the swipe screen ?


    Info:
    Ubuntu 20.04
    Intel Core m5-6Y57 
    Intel® HD Graphics 515
    Xorg
    Intel modesetting Driver. (checked the log at ~/.local/share/xorg/)
    No .conf files for Intel at /etc/X11/xorg.conf.d/ or /usr/share/X11/xorg.conf.d/20-intel.conf

---

### Post by dino99 on 2020-08-10
after getting that video issue, glance at 'journalctl -b' output to know what is going on.

(hopes igpu 515 is not too old to support focal needs)

---

