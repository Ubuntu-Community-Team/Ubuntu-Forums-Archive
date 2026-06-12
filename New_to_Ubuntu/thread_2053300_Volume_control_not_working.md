---
title: "Volume control not working"
date: 2012-09-05
forum: New to Ubuntu
---

### Post by luke21 on 2012-09-05
Hi all,

This is my first post :-)

Before logging in, I am able to adjust the volume. However once logged in, it does not work. Rather i see the speaker and then 3 dashes "---" Please see the attachment for pic.

Sound does work, and I am able to adjust the volume using the keyboard.

Any suggestions?

---

### Post by shreepads on 2012-09-05
Stupid question, what happens when you left click with the mouse on that speaker icon (assuming that's in the top bar)...

---

### Post by 2F4U on 2012-09-05
The icon usually indicates that sound is muted. But if you say that sound works, it is unlikely that it is muted. What does it show when you click on the speaker icon?

---

### Post by luke21 on 2012-09-05
Thanks guys - managed to find the solution here:

[http://askubuntu.com/questions/131307/i-have-sound-but-volume-bar-is-inactive-and-i-cant-use-volume-shortcuts#_=_](http://askubuntu.com/questions/131307/i-have-sound-but-volume-bar-is-inactive-and-i-cant-use-volume-shortcuts#_=_)

"Try killing and restarting pulseaudio, do some /tmp cleaning too. Open terminal and type switch to root using "sudo su" and then do the following:
  killall pulseaudio -KILL
  rm -rf /tmp/pulse-*
  Exit root by pressing CTRL+D and restart pulseaudio by typing: pulseaudio -D
"

---

