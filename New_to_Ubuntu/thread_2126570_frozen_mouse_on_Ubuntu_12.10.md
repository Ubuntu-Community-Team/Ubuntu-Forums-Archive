---
title: "frozen mouse on Ubuntu 12.10"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by llmunro on 2013-03-17
Hello forum!

I'm having a frustrating problem with Ubuntu 12.10 that I don't even know how to start diagnosing: the mouse will seemingly randomly freeze and the only solution seems to be a complete restart of the system.  I can't reproduce it, as it seems to happen at different times, but it seems that it often happens when the mouse is on one of the launcher icons.  The windows of whatever programs I'm using don't seem frozen, as I can still two-finger scroll up and down the launcher, but can't move the mouse otherwise. [FWIW, I've tried switching to Gnome Shell and this still freezes, so I don't think its directly related to the Unity launcher.] This happens approximately 3-4 times a day, which makes it an incredibly annoying problem.  I'm using a Samsung Q430 laptop with Ubuntu 12.10.  I don't recall having this problem with 12.04.

Any ideas, suggestions, or things to check?

Thanks much.
Best,
Lisa

---

### Post by sully101 on 2013-03-17
I dont have this laptop and I'm 12.04 but something to help figure out whats going on might be ```
tail -f | dmesg
```leave it running in a terminal and see if anything happens when you experience problems. Have a look in /var/log/Xorg.0.log or one of the older xorg log files for any warnings ```
cat /var/log/Xorg.0.log | grep WW
```

---

