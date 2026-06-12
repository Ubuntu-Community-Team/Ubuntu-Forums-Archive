---
title: "ubuntu logs me out"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by flOOi!ghenTM on 2008-07-10
I'm having this problem for some time now it's not often but anoing nonetheless.
the system simply logs out just like that. How can i stop it?

10x

---

### Post by sydbat on 2008-07-10
Are you doing anything in particular when this happens? Using a specific application, for example?

---

### Post by flOOi!ghenTM on 2008-07-10
No it just happens very random, sometimes i'm just reading something on the web and boom.

---

### Post by sydbat on 2008-07-10
There should be something in the logs to give you a clue, like an error message just before a random log out. System > Administration > System Log. Look for the time around the last random log out (or wait for the next one) and see if something error related shows up. Then let us know. 

Sorry about not being super technical, I'm learning too!

---

### Post by flOOi!ghenTM on 2008-07-10
afexactly after my last post it loged me out again and here is what i got

> Jul 10 20:08:18 HARVEST -- MARK --
Jul 10 20:12:11 HARVEST kernel: [ 1517.457436] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Jul 10 20:12:12 HARVEST kernel: [ 1517.457528] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
Jul 10 20:12:12 HARVEST kernel: [ 1517.457579] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
Jul 10 20:12:32 HARVEST pulseaudio[6223]: pid.c: Stale PID file, overwriting.
Jul 10 20:12:33 HARVEST pulseaudio[6223]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
Jul 10 20:12:33 HARVEST pulseaudio[6223]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.

---

### Post by sydbat on 2008-07-10
Can you look back in your logs to previous times you got auto logged out and see if there are similar lines? It might be your video card or the audio drivers not liking something.

Also, if anyone else knows something CLI to help diagnose the problem, I would appreciate the help.

---

### Post by flOOi!ghenTM on 2008-07-10
i found that the pulseaoudio log is repeatinf itself very often 
```
Jul 10 19:21:52 HARVEST pulseaudio[6773]: pid.c: Stale PID file, overwriting.
Jul 10 19:21:52 HARVEST pulseaudio[6773]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jul 10 19:21:52 HARVEST pulseaudio[6773]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
```

---

