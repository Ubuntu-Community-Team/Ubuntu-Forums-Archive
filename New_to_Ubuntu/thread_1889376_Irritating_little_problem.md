---
title: "Irritating little problem"
date: 2011-12-01
forum: New to Ubuntu
---

### Post by Non-Sequitur on 2011-12-01
Irritating little problem.

I have a Logitech B-500 camera.  It works fine in Ubuntu 11.10.  However, any time I perform an update, I HAVE to reboot the computer in order to get the webcam microphone to work.  The camera and audio out does not fail, just the mic.  As I said, not a game stopper but it is an irritant.  Anyone else have that problem as well as a solution?  :)

---

### Post by lechien73 on 2011-12-01
I had a similar issue with the internal webcam on my wife's laptop.

I had to install the PulseAudio Volume Control:

```
sudo apt-get install pavucontrol
```

and then set the defaults for the microphone from there. I don't know why, but the mic always ends up muted after an update.

---

### Post by Non-Sequitur on 2011-12-01
Thanks but no joy.  Problem remains.

---

