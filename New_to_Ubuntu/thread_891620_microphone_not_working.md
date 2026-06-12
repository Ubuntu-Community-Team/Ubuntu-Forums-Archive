---
title: "microphone not working"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-08-16
my ubuntu 8.04 doesn't capture sound from the microphone,even though i have unmuted the microphone and cranked up its volume from the volume control.

---

### Post by stonecoldjha on 2008-08-16
i also tried changing my preferences in devices tab(from preferences>sound),but to no avail.

---

### Post by stonecoldjha on 2008-08-16
i am absolutely helpless,i couldn't get it to work

---

### Post by eram on 2008-08-16
is it a built in microphone?

---

### Post by stonecoldjha on 2008-08-16
nopes,its an external microphone attached to my headphone,connected through a jack.

---

### Post by eram on 2008-08-16
through which jack?

---

### Post by stonecoldjha on 2008-08-16
through the pink one.microphone does work well in windows xp.

---

### Post by eram on 2008-08-16
do you have any other device that connects through either the pink or the blue jack?

---

### Post by stonecoldjha on 2008-08-16
well seriously,does microphone even work on ubuntu hardy...........i am frustrated.faced zillions of problems right since the installation,even changed my graphics card to a new nvidia one,pimped up the GUI with emerald,compiz,cairo dock,some screenlets to outperform vista,or i would say even mac osx,in terms of looks,i really appreciate the way ubuntu performs on my machine,its crazy fast and way too responsive..........but here i am stuck,despite so much of eyecandy and commendable performance the microphone doesn't work at all,which is totally unaccepatable to me.............please help.

---

### Post by eram on 2008-08-16
yes, microphone does work on hardy because I use it all the time.

---

### Post by eram on 2008-08-16
could you post the out put of ```
amixer
```

---

### Post by stonecoldjha on 2008-08-16
here is the output of amixer:

[B][SIZE="4"]sonu@sonu-desktop:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-46.50dB] [on]
  Front Right: Playback 0 [0%] [-46.50dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-46.50dB] [on]
  Front Right: Playback 0 [0%] [-46.50dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [on]
  Front Right: Capture 0 [0%] [-16.50dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [on]
  Front Right: Capture 0 [0%] [-16.50dB] [on]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 60 [50%] [0.00dB]
  Front Right: Capture 60 [50%] [0.00dB]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Line' 'CD'
  Item0: 'Mic'
sonu@sonu-desktop:~$ 

[/SIZE][/B]

---

### Post by stonecoldjha on 2008-08-16
kindly help me get it working,i have got sick of booting into windows when i need microphone.

---

### Post by stonecoldjha on 2008-08-16
hello,i would sincerely appreciate if i am helped.........thanks in advance,so far my microphone is unyielding .

---

### Post by eram on 2008-08-16
```
alsamixer
``` Go into the playback "tab" and mute mic. Go into the capture tab, I think f4 and hit space on Mic and space on capture until L R Captur is red under both Mic and Capture. make sure you turn up the volume using the up arrows.
Also try unmuting the Mic booster: should be right next to the Mic option in alsamixer.

---

