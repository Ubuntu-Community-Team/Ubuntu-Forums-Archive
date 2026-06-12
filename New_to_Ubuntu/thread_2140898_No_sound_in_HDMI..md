---
title: "No sound in HDMI."
date: 2013-05-01
forum: New to Ubuntu
---

### Post by KaustubhShamshery on 2013-05-01
I have ubuntu 13.04 and and using dual monitor. I want the sound to come from the other monitor (built in speakers) which is connected with HDMI. How do i do it?

---

### Post by pqwoerituytrueiwoq on 2013-05-01
click on the volume icon (near the clock) -> sound settings -> configuration
you can figure it out from there
if you have no hdmi option
use this: [https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme)
if it still does not work add this ppa and check for updates and upgrade
[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa)

---

### Post by zeljkojagust on 2013-05-01
Install alsamixergui package (sudo apt-get install alsamixergui).
Start alsamixer in terminal and check if you have S/PDIF or similar sound bar. Below it should be [MM] or [00]. If it's [MM], press m to unmute digital output and you'll have sound.

---

