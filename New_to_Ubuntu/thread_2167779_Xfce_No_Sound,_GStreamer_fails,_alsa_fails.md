---
title: "Xfce No Sound, GStreamer fails, alsa fails"
date: 2013-08-15
forum: New to Ubuntu
---

### Post by g2geo94 on 2013-08-15
So due to complications which I will not get into on the account of irrelevancy, I installed ubuntu today from a 32bit Server install, 12.04.2 LTS (rather than the desktop equivalent, of course). I then proceeded to install xfce4 and xserver-xorg for a working, yet simple, DE. Since then, I have had few complications, but the most frustrating, and the object of this thread, is the lack of sound. I've done an hour's worth of Googling, trying all that was suggested. No avail.

Alsa is installed, gstreamer0.10, its plugins including restricted, ubuntu restricted, and I am in fact, part of the "audio" group. In fact, I set my self to an "Administrator" in the Users and Groups manager.
alsamixer can be launched from shell as root, but
```
alsamixer
cannot open mixer: No such file or directory

```happens as user.
GStreamer's little panel control and the mixer in menu both report 
```
GStreamer was unable to detect any sound devices. Some sound system specific GStreamer packages may be missing. It may also be a permissions problem.
```

And all troubleshooting steps above were completed prior to a recent reboot which also did not fix the problem.
I'm not a complete beginner to Ubuntu nor Linux, but to Xfce and scratch DE installs, I might as well be in the heart of Japan with Portuguese as my only known language.

Help is appreciated, thanks in advance.
Geoffrey.

---

