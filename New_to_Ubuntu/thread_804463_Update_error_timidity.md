---
title: "Update error: timidity"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by MadsRH on 2008-05-23
Hi
I get this error every time I do an update, and I don't know what Timidity is!

Can anyone tell me how to get rid of the error?

```
"E: timidity: underproces post-installation script returnerede afslutningsstatus 1"
```
[B]
MadsRH[/B]

---

### Post by marufaberlin on 2008-05-23
you need timidity for midi playback. If you don't need that, try  *sudo apt-get purge timidity*, but I wouldn't recommend that. There's also always sudo dpkg --configure -a

---

### Post by MadsRH on 2008-05-23
Okay, MIDI playback - I do need that!

If I try to do a ```
sudo dpkg --configure -a
``` I get the same error!

---

### Post by marufaberlin on 2008-05-23
what's the full output?

---

### Post by MadsRH on 2008-05-23
Some of this is in Danish:

```
Sætter timidity (2.13.2-19ubuntu1) op...
 * Starting TiMidity++ ALSA midi emulation...                            [fail] 
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: fejl under behandling af timidity (--configure):
 underproces post-installation script returnerede afslutningsstatus 1
Der opstod fejl under behandlingen:
 timidity

```

---

### Post by marufaberlin on 2008-05-23
ok, try this:

timidity -iA

if it works, regard this error as nothing more than an annoyance.  You have a problem with your runlevel startup files, which is pretty common. The only effect is that timidity won't start with bootup, which you can fix with update-rc, or start it manually using timidity -ia. (please regard case sensitivity)

---

### Post by MadsRH on 2008-05-23
```
TiMidity starting in ALSA server mode
Opening sequencer port: 129:0 129:1 129:2 129:3

```

So no error, but it still isn't working!

```
Sætter timidity (2.13.2-19ubuntu1) op...
 * Starting TiMidity++ ALSA midi emulation...                            [fail] 
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: fejl under behandling af timidity (--configure):
 underproces post-installation script returnerede afslutningsstatus 1
Der opstod fejl under behandlingen:
 timidity

```

What do you mean by update-rc??? I'm kind of a newbie so you need to be very bold :(

---

### Post by marufaberlin on 2008-05-23
when your computer starts, some scripts are run to start programs at different stages of the boot. these files are rc files and can be edited, in ubuntu you use a program called update-rc. Like I said, the error is not important, you can ignore it. It's just a nuisance.

---

### Post by MadsRH on 2008-05-23
Okay, thanks for helping out :)

---

### Post by marufaberlin on 2008-05-25
mark thread as solved, then.

---

