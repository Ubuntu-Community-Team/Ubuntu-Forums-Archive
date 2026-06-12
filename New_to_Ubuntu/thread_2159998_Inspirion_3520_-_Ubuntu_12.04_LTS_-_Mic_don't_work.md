---
title: "Inspirion 3520 - Ubuntu 12.04 LTS - Mic don't work"
date: 2013-07-05
forum: New to Ubuntu
---

### Post by muahlers on 2013-07-05
Hello,

I bought a Inspirion 3520 for XMS, and I installed on it a Ubuntu 12.04 LTS partition. Almost everything work on it, except my microphone. I can't use it. This is a big issue for me because I need to use Sky and Google hang out regulary!

I probe a lot of things, even I installed the ubuntu audio dev repository->([https://launchpad.net/~ubuntu-audio-dev/+archive/ppa](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa))

But nothing seems to work.

If someone could help me I will be really glad!

---

### Post by halimm4m on 2013-07-05
hello,
this is my first post in this forum I hope it will help, try to check the sound setting: system settings-->sound-->input turn the mic on if it is off and try to increase the input volume.

---

### Post by ajgreeny on 2013-07-05
Run ```
alsamixer
``` in terminal and check that the levels of outputs or inputs are not set too low or muted.
Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
In capture page use spacebar to enable the different input devices (mic, line, CD, video).
Esc will save and exit.

---

