---
title: "Ubuntu 11.10 VLC Audio Nightmare"
date: 2011-11-05
forum: New to Ubuntu
---

### Post by slayner117 on 2011-11-05
Okay, So what I am doing, is simply trying to watch TV on my 32" Samsung TV using an HDMI cable as the link to make it a monitor. The Video display is fine and audio for things such as online games, youtube videos and even Movies played with other applications work fine. I suppose it's a pet peeve of mine but I really prefer VLC. 

What's basically happening is that when playing any video using VLC (with the audio set to come through the television instead of my computer speakers) The delay is outstanding, and the audio is... Very scratchy.

Please help me out with this issue. Thank you in advance.

---

### Post by slayner117 on 2011-11-05
I forgot to mention, I had this same setup on 11.04 and it worked just fine.

---

### Post by 4Orbs on 2011-11-05
This fixed my audio problems on 11.04 and 11.10. Just edit one file, and easy to un-do if it doesn't fix your problem.

To open the file /etc/pulse/default.pa in a text editor (as administrator), enter this in the terminal:
```
sudo gedit /etc/pulse/default.pa
```
and find this line in the file:
```
load-module module-udev-detect
```
and add the bit at the end, so the line looks like this:
```
load-module module-udev-detect tsched=0
```
Then save the file and close it. Reboot and see if it worked.

---

### Post by slayner117 on 2011-11-05
Thanks, It worked just fine.

---

### Post by shashikunal on 2011-11-05
> **slayner117 said:**
> Okay, So what I am doing, is simply trying to watch TV on my 32" Samsung TV using an HDMI cable as the link to make it a monitor. The Video display is fine and audio for things such as online games, youtube videos and even Movies played with other applications work fine. I suppose it's a pet peeve of mine but I really prefer VLC. 

What's basically happening is that when playing any video using VLC (with the audio set to come through the television instead of my computer speakers) The delay is outstanding, and the audio is... Very scratchy.

Please help me out with this issue. Thank you in advance.
sudo apt-get install vlc

---

### Post by DreamMastR on 2011-12-25
This helped me as well.  Thank you! :D

---

### Post by aleeg on 2012-04-25
It works like a charm, thank you.

---

