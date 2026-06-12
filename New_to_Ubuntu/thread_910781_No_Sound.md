---
title: "No Sound"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by john.hall on 2008-09-04
Sometimes when I play an mp3 or avi, then close it (either because the player somehow crashed or hung, or the mp3/avi played to completion) and I try to open another one, there is no sound.  The bar on the player goes, and the sound is up.  There should be sound, but its like the sound card is hung or something.

I'm not exactly sure what is causing this.  I've tried using several different media players, including Totem, Amarok, and VLC.  As far as I can tell, it happens with all of them.  I have Realtek HD integrated sound on my MSI P31 Neo motherboard.

Like I said, it works when I first start, but then something happens (I don't know what changes) and I have to reboot to get sound back.  Is there a reason for this problem or perhaps a workaround?  Is there a way to restart the sound without restarting the entire machine?

---

### Post by scragar on 2008-09-04
it's another pulse audio problem, the thing locks sound to a single program, and when that program doesn't quit correctly pulse can just get caught waiting for more input from a process that doesn't exist, blocking almost all sound. :(

the easy solution, is to just press alt+F2 for the run box, then type```
killall pulseaudio
``` although this is a temporary solution(since pulse will start again when you restart).

---

### Post by john.hall on 2008-09-04
Is there a command line equivalent of chkconfig in Ubuntu, or do I have to permanently disable pulseaudio through bum?

---

### Post by scragar on 2008-09-04
there are a few ways to disable pulse audio perminantly and use M-audio instead, but this results in a loss of system sounds, so the best solution(to me anyway), is to just add that command into the statup applications found in System>Preferences>Sessions

---

