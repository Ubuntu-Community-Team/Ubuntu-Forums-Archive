---
title: "Multimedia keys issue for music"
date: 2012-03-27
forum: New to Ubuntu
---

### Post by mkondalwadikar on 2012-03-27
Hi...I am using Audacious player for my music and I have a Logitech multimedia keyboard. But apart from Volume control, no other keys seem to work eg. the next and previous song buttons.

Is there anyway to make this happen. Thanks :)

---

### Post by Kevin McCready on 2012-03-27
I wiped out Audacious and installed gnome-media and use mplayer ((I had to install PulseAudio Volume Control and then select Sound Recorder) but am very happy with the result. with

---

### Post by Kevin McCready on 2012-03-27
PS
The way I did it on Lubuntu was:
open a terminal with ctrl-alt-t, then I type

```
sudo apt-get update
```
then put in my password. 

then
```
sudo get-apt install gnome-media
```

Then I reboot just to make sure it all sticks. And the menu system has mplayer in it

---

