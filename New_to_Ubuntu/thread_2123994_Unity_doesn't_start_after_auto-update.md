---
title: "Unity doesn't start after auto-update"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by rounder8 on 2013-03-09
I just installed fresh copy of Ubuntu 12.10 (64-bit).

I ran auto-update (293 updates) and it asked to reboot the system. After restarting start-up process freezes on Starting [OK] and nothing happens.
I did ctrl+alt+f1 to access terminal. I tried:

startx

That launched the desktop without sidebars or nothing. Just the plain background image.

I tried ctrl+alt+t and I was able to launch terminal. I'm clueless how to proceed from here?

What went wrong with the auto-update?

---

### Post by rounder8 on 2013-03-09
Strange, I restarted the computer and now it booted to Unity without problems. Why didn't it restart to the graphical interface on the first trial? In case if this happens again is there some command to start Unity (with sidebars and everything), startx didn't do it. Or should I just try to restart again?

---

### Post by arpanaut on 2013-03-09
The command to reset Unity with 12.10 is 

```
setsid unity
```

---

### Post by fiodev on 2013-03-09
do the ctrl+alt+f1 things again
apt-get install gdm

---

### Post by arpanaut on 2013-03-09
> **fiodev said:**
> do the ctrl+alt+f1 things again
apt-get install gdm
Ubuntu with Unity shell desktop uses lightdm so that would not be the solution to this situation.

---

