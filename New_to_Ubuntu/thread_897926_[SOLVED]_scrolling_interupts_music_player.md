---
title: "[SOLVED] scrolling interupts music player"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by maxvonager on 2008-08-22
When using the mouse wheel to scroll,my music player (rhythmbox) will
pause, and then continue when the scrolling is stopped. Any suggestions?
Also...very simple question...How do I create a picture file in the format needed to use to customize my login screen. I tried to create an archive, but it is not recognized.Thank you

---

### Post by bubba_169 on 2008-08-22
Just out of interest, what are the specs of the computer you're running ubuntu on (ie CPU speed/type, RAM.) It's only that I remember I had the same audio problem with windows 98 a long time ago when my specs were a bit poor.

---

### Post by whitethorn on 2008-08-22
Hi I had a problem a little like yours. Running this command got rid of the skips for me, hope it helps.


```

sudo /etc/init.d/alsa-utils reset
```

---

### Post by kk0sse54 on 2008-08-22
You could also try a different media player to see if you still get the same problem as I know I had performance problems with Rhythmebox because of my large library

---

### Post by maxvonager on 2008-08-22
The stats...intel celeron 2.5g   1g memory  . Thank you. It was a Dell running windows xp before I killed it and installed linux. I am running Ubuntu Hardy.

---

