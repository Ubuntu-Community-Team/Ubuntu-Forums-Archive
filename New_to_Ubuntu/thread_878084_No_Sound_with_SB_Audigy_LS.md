---
title: "No Sound with SB Audigy LS"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by Brainal on 2008-08-02
I've tried pretty much everything! Ubuntu can see it fine, it's just that I can't hear anything. The Alsa CA0106 drivers are active and I still get no sound. I also put in "alsamixer" in terminal and turned everything up and unmuted it. Any thoughts?


And here's what I get when I enter "sudo lshw -C multimedia"
```
*-multimedia            
       description: Multimedia audio controller
       product: SB Audigy LS
       vendor: Creative Labs
       physical id: 8
       bus info: pci@0000:04:08.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=CA0106 latency=64 maxlatency=20 mingnt=2 module=snd_ca0106
  *-multimedia
       description: Audio device
       product: MCP51 High Definition Audio
       vendor: nVidia Corporation
       physical id: 10.1
       bus info: pci@0000:00:10.1
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
```

---

### Post by blastus on 2008-08-02
Have you tried turning the switches on/off in Volume Control? I had a computer with a SoundBlaster Audigy (the first version) and I usually had to turn a switch called "Digital" or something like that on or off to get sound after installing Ubuntu. On my laptop I also have to mess with switches to get sound.

---

