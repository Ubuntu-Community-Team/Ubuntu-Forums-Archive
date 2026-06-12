---
title: "The screen will cause Z distortion after rotating"
date: 2019-08-07
forum: New to Ubuntu
---

### Post by brentko on 2019-08-07
After screen rotation, the screen display will cause Z distortion when playing video or quickly switching photos.


We tried several monitors. ENVIRONMENT: Display = HDMI/DP Resolution = 1920x1080p / 1920x1920 OS = Ubuntu 18.04, Kernel 4.18.20 Platform: Intel Apollo Lake N4200


STEP: 1. System boot up 2. Rotation display to left/right/inverted 3. Play video


rotate to the right, Z distortion happen
$ xrandr -o right


rotate to the upside down, Z distortion happen
$ xrandr -o inverted


rotate to the left, Z distortion happen
$ xrandr -o left


rotate to the normal
$ xrandr -o normal


RESULT: screen will cause Z distortion. see the recording video below: 
[https://drive.google.com/drive/folders/15oDuXqsMn8Q-39K8StbfkuBeL_CWF584?usp=sharing](https://drive.google.com/drive/folders/15oDuXqsMn8Q-39K8StbfkuBeL_CWF584?usp=sharing)

---

