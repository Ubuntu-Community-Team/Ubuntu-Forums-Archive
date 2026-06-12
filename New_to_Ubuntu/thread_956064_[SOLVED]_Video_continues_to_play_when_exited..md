---
title: "[SOLVED] Video continues to play when exited."
date: 2008-10-22
forum: New to Ubuntu
---

### Post by mike_pasara on 2008-10-22
I was watching a video in VLC and decided to stop watching it. I closed the video by pressing X in the top right corner like I would always do. I can still hear audio playing even with the application closed. I checked my other desktop on the switcher and it's not there. What's the deal? The video is done playing but I have a feeling the process is still running. 

I'm using 8.04 64 bit.

---

### Post by PocketDog on 2008-10-22
Stop the video before closing VLC and that shouldn't happen. To kill the sound if VLC doesn't close properly type **killall vlc** in Terminal

---

### Post by mike_pasara on 2008-10-22
ok cool


is there like an alt+control+delete command for ubuntu, that way i can check if the process is still running. It could also serve useful in the future.

---

### Post by PocketDog on 2008-10-22
In terminal type **top**. Kill any unwanted processes with (obviously) **killall *processname***

---

### Post by mike_pasara on 2008-10-22
no keyboard shortcut?

---

### Post by PocketDog on 2008-10-22
It looks possible

[http://www.ubuntu-unleashed.com/2007/08/howto-alt-ctrl-del-ubuntu-task-manager.html](http://www.ubuntu-unleashed.com/2007/08/howto-alt-ctrl-del-ubuntu-task-manager.html)

Good luck!

---

