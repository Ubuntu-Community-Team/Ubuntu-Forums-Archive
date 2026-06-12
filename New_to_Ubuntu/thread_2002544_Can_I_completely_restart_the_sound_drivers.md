---
title: "Can I completely restart the sound drivers?"
date: 2012-06-12
forum: New to Ubuntu
---

### Post by Ultrelusive on 2012-06-12
Hey guys, I was trying to assign a mute toggle command to a button on my keyboard, and used sudo amixer sset Master toggle. It muted the sound, but it won't turn back on. I've restarted the computer to no avail. 

sudo amixer -c 0 set Master 1+ unmute didn't work either.

Is there a way to completely restore the sound drivers, or another way to get my volume back? I'm using Xubuntu 12.04

Cheers

---

### Post by Ultrelusive on 2012-06-12
Also, alsamixer reports that all the volume controls are turned up

---

### Post by Jose Catre-Vandis on 2012-06-12
Here is your answer: [http://bimma.me.uk/2012/03/01/xubuntu-1110-volume-mute-button/](http://bimma.me.uk/2012/03/01/xubuntu-1110-volume-mute-button/)
Works fine for me on Xubuntu 12.04 as a keyboard shortcut or launcher
(originaLLY from this forum, Toz, iirc)

---

### Post by Ultrelusive on 2012-06-12
That didn't work unfortunately. I think it just assigned the mute toggle to the key again without fixing the underlying reason why the sound won't come back on

---

### Post by Jose Catre-Vandis on 2012-06-12
Did you use:```
amixer set Master toggle
```
(not sset). No need for sudo.
Also check your "Master" is actually called Master.

When you run alsamixer in a terminal you should now see that the default sound card is called PulseAudio and there is only one meter - Master.

Terminal output from running the command:
```
~$:amixer set Master toggle
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 65536 [100%] [off]
  Front Right: Playback 65536 [100%] [off]
~$ amixer set Master toggle
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 65536 [100%] [on]
  Front Right: Playback 65536 [100%] [on]

```

I also have xfce4-mixer installed to provide a halfway house between pavucontrol and alsamixer ;)
```
sudo apt-get install xfce4-mixer
```

---

### Post by Ultrelusive on 2012-06-13
> **Jose Catre-Vandis said:**
> Did you use:```
amixer set Master toggle
```
(not sset). No need for sudo.
Also check your "Master" is actually called Master.

When you run alsamixer in a terminal you should now see that the default sound card is called PulseAudio and there is only one meter - Master.

Terminal output from running the command:
```
~$:amixer set Master toggle
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 65536 [100%] [off]
  Front Right: Playback 65536 [100%] [off]
~$ amixer set Master toggle
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 65536 [100%] [on]
  Front Right: Playback 65536 [100%] [on]

```

I also have xfce4-mixer installed to provide a halfway house between pavucontrol and alsamixer ;)
```
sudo apt-get install xfce4-mixer
```

Worked a charm thanks!

---

### Post by Jose Catre-Vandis on 2012-06-13
:cool:Ah good, we got there in the end.

Forgot to mention a restart of sound services (or reboot) may be necessary.

---

