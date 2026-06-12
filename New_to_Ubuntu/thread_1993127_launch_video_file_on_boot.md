---
title: "launch video file on boot"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by DHinton on 2012-06-01
I am trying run a video file on boot, I would like it to be full screen and to loop.  Currently it is a .mov file but I could change that if that makes it easier.  I did try mplayer -fs myvideo.mov, but that did not do anything.  I am using 12.04 LTS.  Thanks

---

### Post by ajgreeny on 2012-06-01
Perhaps that is trying to run too soon after the session starts and before the GUI is up and running properly.

Try command ```
bash -c "sleep 10; mplayer -fs myvideo.mov"
``` in the command box of the startup applications.  The delay of 10 seconds may make it work OK, and if so you can reduce the sleep time to get the lowest figure that still works.

---

### Post by DHinton on 2012-06-01
> **ajgreeny said:**
> Perhaps that is trying to run too soon after the session starts and before the GUI is up and running properly.

Try command ```
bash -c "sleep 10; mplayer -fs myvideo.mov"
``` in the command box of the startup applications.  The delay of 10 seconds may make it work OK, and if so you can reduce the sleep time to get the lowest figure that still works.
didn't seem to help :(

---

### Post by Cheesemill on 2012-06-01
Does
```
mplayer -fs myvideo.mov
```
work OK if you run it from a terminal manually?

You could also try using the full  paths and see if that makes a difference, for example:
```
/usr/bin/mplayer -fs /home/username/Videos/myvideo.mov
```

---

