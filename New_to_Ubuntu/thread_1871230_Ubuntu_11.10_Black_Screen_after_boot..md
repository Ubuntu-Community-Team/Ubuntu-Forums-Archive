---
title: "Ubuntu 11.10 Black Screen after boot."
date: 2011-10-28
forum: New to Ubuntu
---

### Post by Rave Gloves on 2011-10-28
I installed ubuntu 11.10 on to a netbook. It booted fine for a couple of restarts but now the screen goes purple as it is going to boot and the ubuntu sign pops up for a split second and the screen goes black. [This]("http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-11-10-black-screen-after-boot-screen-908044/")thread sounds like my problem but if i type in my password i will hear the log in sound. I'm assuming this might be a video card error of some kind. Anyone else had the same kind of problem?.

---

### Post by Rave Gloves on 2011-10-28
Small update, i managed to get onto recovery mode and ran ```
sudo dpkg --configure -a
```
And it gave me this error ```
error: unable to access dpkg status area: Read-only file system
```

---

### Post by Rave Gloves on 2011-10-28
Another quick update. I suspect it is a graphical issue. I put in the usb pen to try and see if i could do a fresh install. The purple screen comes up with what i think is a keyboard sign then it just goes black again but again, i can still here certain log in noises. I have no idea why a graphics card could fail with installing ubuntu 11.10. I really doubt it is the graphics card but to me it's looking that way.

---

