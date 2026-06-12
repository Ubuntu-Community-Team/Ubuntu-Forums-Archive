---
title: "No sound through HDMI using AMD Radeon 7750"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by jalopezp on 2012-11-04
Hi! I'm using an AMD Radeon 7750 and have connected it to my television through an HDMI cable. Sadly, I get no sound, and can't even see HDMI as an output device on Sound Settings: [IMG]http://i.imgur.com/twcA3.png[/IMG]. I have the standard fglrx drivers installed and have added the radeon.audio=1 option to /etc/default/grub. Here I've run some commands (let me know if code is not the right markup for this):

```
sudo aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v | grep -A7 -i "audio"

00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
    Subsystem: ASRock Incorporation Device 8892
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f7f10000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

--
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device aab0
    Subsystem: Giga-byte Technology Device aab0
    Flags: fast devsel, IRQ 17
    Memory at f7e60000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel

```I fear I may be missing some basic configuration, I'm really quite new at linux. But on the other hand, I found [this bug]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1014074") which is possibly affecting me, just like the [fourth comment]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1014074/comments/4"). 

Thanks very much for any help. I realise the problem is very common, there are many threads on the subject, but most solutions seem to be installing the drivers and  editing the grub config. 

I've just set up my computer this week and I've enjoyed it quite a bit. It's a bit sad that I don't get to play with it as much while I'm still trying to get it to work properly :-( but it's great how quickly one gets up to speed just by trying to solve a particular problem. Cheers!

---

### Post by geomcd1949 on 2012-11-04
Same problem. Same attempted solutions. Same lack of joy.

If I find a solution I'll post it here.

~George

---

### Post by jalopezp on 2012-11-05
Thanks, George, I really appreciate it. Hope you sort it out! :-)

Can anyone tell me a bit more about ALSA and how to troubleshoot it? Following the steps in procedure Ac [here](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1#heading=h.slxd612cf14e), it does seem like my sound card (the one onboard my AMD graphics card) is recongnised by ALSA and has been activated. But on the other hand, I would expect ```
aplay -l
``` to display *some* reference to HDMI. 

Am I wrong? Is ```
aplay -l
``` displaying the right thing? 

Thanks again.

---

