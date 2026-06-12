---
title: "Camera Help"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by nicholas mccarthy on 2008-11-05
Hello,

I'm having trouble accessing my digital camera. Whenever I try to use it, this comes up:

"Unable to mount Nikon Corp. Coolpix 4600 (ptp)

Error initializing camera: -1: Unspecified error"

Any help?

---

### Post by nicholas mccarthy on 2008-11-05
Anyone got any help? It used to work whenever I plugged it in, but now this error is coming up.

---

### Post by OwnSurname on 2008-12-14
Same problem here (with Coolpix 5600 though), please if you've a solution, just let us know. I'm going crazy.

---

### Post by OwnSurname on 2008-12-14
Actually, the solution is here:

[http://www.uluga.ubuntuforums.org/showthread.php?t=1003745](http://www.uluga.ubuntuforums.org/showthread.php?t=1003745)

Basically the camera has 2 mode in the setup menu for the USB:
* USB mass storage
* USB Picture Transfer Protocol
setting the camera on the second works under Intrepid, although the first one worked under Hardy perfectly.

---

### Post by RomanIvanov on 2008-12-14
use "f-spot" application to work with cams, it helped me:
```
sudo apt-get install f-spot
```

---

