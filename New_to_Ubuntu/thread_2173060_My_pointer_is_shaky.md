---
title: "My pointer is shaky"
date: 2013-09-07
forum: New to Ubuntu
---

### Post by steve-q32 on 2013-09-07
Just installed Ubuntu 13.04 via disk to HP Pavillion g6. I think It's great but the pointer is a bit jittery and difficult to position accurately. Tried adjusting pointer speed in settings but that didn't work. Is there a way to adjust pointer sensitivity? Thanks.

---

### Post by Drone4four on 2013-09-07
You could try fiddling around with the options in gpointing-device-settings.  To install, open a terminal and use this:```
sudo apt-get install gpointing-device-settings
```  More in depth instructions [here]("http://askubuntu.com/questions/42867/modifying-mouse-touchpad-sensitivity").

---

### Post by smirnich on 2013-09-08
This post solved my touchpad problems: [http://ubuntuforums.org/showthread.php?t=1971259](http://ubuntuforums.org/showthread.php?t=1971259)

Try increasing the values of Horizhysteresis and VertHysteresis in Terminal (copy and paste from the aforementioned thread):

[COLOR=#000000]synclient HorizHysteresis=72 (you can add whatever value you want to test the behavior of your touchpad, for me 72 is fine)[/COLOR]
[COLOR=#000000]synclient VertHysteresis=72 (you can add whatever value you want to test the behavior of your touchpad, for me 72 is fine)

If you want to make the change permanent, see the last comment in that thread.[/COLOR]

---

