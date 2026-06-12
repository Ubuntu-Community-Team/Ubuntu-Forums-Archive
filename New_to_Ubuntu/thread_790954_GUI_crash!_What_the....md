---
title: "GUI crash! What the..."
date: 2008-05-11
forum: New to Ubuntu
---

### Post by ant2ne on 2008-05-11
I was minding my own buisines messing around with wine when I pressed Cntl+Shift+Alt+F10 (or was it F11) and poof I got a black screen with a flashing cursor. I couldn't type anything though. So I restarted the computer. I can log in to a text terminal session, but I can not get my gui desktop to come back up.

I read this [http://ubuntuforums.org/showthread.php?t=577998](http://ubuntuforums.org/showthread.php?t=577998) but it is no help. Cntl + Alt + F7/F1 are not helping.

How do I recover?

---

### Post by macaholic on 2008-05-11
You went into whats called a tty, or virtual terminal. To get back to your GUI just do a ctrl + alt + F7. The tty terminals are accesed via these keystrokes, and you use them when your gui isn't working, or for various other more complicated purposes.

---

### Post by ant2ne on 2008-05-11
> **ant2ne said:**
> Cntl + Alt + F7/F1 are not helping.Let me rephrase that. Cntl  + Alt + F7 is not working. This takes me to the virtual terminal thingy. Which doesn't help. From there, I can press Cntl  + Alt + F7 again, which does nothing. Or I can press Cntl  + Alt + F1 and go back to the command line.

---

### Post by dizee on 2008-05-11
Try typing ```
startx
``` and see if it works.

---

### Post by ant2ne on 2008-05-12
i type startx
```

xauth: creating new authority file /home/ant2ne/.Xauthority
xauth: creating new authority file /home/ant2ne/.Xauthority

.etc.X11.X us bit executable
giving up.
xinit: no such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error
```
(back to prompt)

Re-install time?

---

### Post by Canis familiaris on 2008-05-12
Try reconfiguring your X-server:
```
sudo dpkg-reconfigure xserver-xorg
```

---

