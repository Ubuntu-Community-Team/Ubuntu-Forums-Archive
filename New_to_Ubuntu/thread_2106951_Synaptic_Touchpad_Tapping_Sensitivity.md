---
title: "Synaptic Touchpad Tapping Sensitivity"
date: 2013-01-20
forum: New to Ubuntu
---

### Post by cylent on 2013-01-20
My HP Pavilion DV7 laptop has a touchpad. So far so good. 
Unfortunately its the Synaptic kind. The most hated one for Linux users.

In ubuntu 12.10 its sensitivity is literally CRAP. i can move the cursor around and that's great but come to start to "Tap-click" and its never precise. it bounces around when tapping and its soooooooo annoying. it makes me hate using my computer altogether. 

In windows of course this issue doesnt exist.

I found this workaround on this page however the solution is somewhat hard to tweak. [http://superuser.com/questions/229839/reduce-laptop-touch-pad-sensitivity-in-ubuntu](http://superuser.com/questions/229839/reduce-laptop-touch-pad-sensitivity-in-ubuntu)

if anyone knows of a utility that will make this somewhat fixable please advise.

I really want to have ubuntu on my laptop.

((edit: i seem to have found a working value that works for me: **```
xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Finger" 55 60 255
```**))

---

