---
title: "ASUS u2e graphics &amp; Sound problem"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by hp3 on 2008-06-09
Ubuntu 8.04 64 bit alternate cd used for install.

I have an ASUS u2e Video works, but Ubuntu does not detect that this is a wide sceerrn laptop. (see pictues attached), so every ting is always displayed on the left side of my screen. and the panels only conver 70% of my screen. 

No sound but I found a thread on another forum that said:

snd-hda-intel must be changed to lenovo

But I am unable to find out where it should be changed.

I have tried to follow the sound sticky forumpost, but it seams to be for ALSA, and I think ubuntu now uses puls-audio?

I have tried this for two weeks now, but have bean unable to find a solution.  Tried posting in the multimedia form but, I must have done something wrong, got no replay to my question.  

lspci output:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller
(rev 03)
Subsystem: ASUSTeK Computer Inc. Unknown device 1783
Flags: bus master, fast devsel, latency 0, IRQ 22
Memory at fe9f8000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>



00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrat
ed Graphics Controller (rev 03) (prog-if 00 [VGA controller])
Subsystem: ASUSTeK Computer Inc. Unknown device 14e2
Flags: bus master, fast devsel, latency 0, IRQ 16
Memory at feb00000 (64-bit, non-prefetchable) [size=1M]
Memory at e0000000 (64-bit, prefetchable) [size=256M]
I/O ports at ec00 [size=8]
Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Grap
hics Controller (rev 03)
Subsystem: ASUSTeK Computer Inc. Unknown device 14e2
Flags: bus master, fast devsel, latency 0
Memory at fea00000 (64-bit, non-prefetchable) [size=1M]
Capabilities: <access denied>

I hope somone can help me out.

---

### Post by faktorqm on 2008-06-10
Hello!!

To fix the video issues you can try go to Applications -> Accesories -> Terminal and type

```
sudo displayconfig-gtk
```

To fix the sound issues, install linux-backports-modules and modify /etc/modprobe.d/alsa-base to include the setting for Intel HD Audio controller. 

1) ```
sudo aptitude install linux-backports-modules
```
2) ```
sudo gedit /etc/modprobe.d/alsa-base
```

options snd-hda-intel model=lenovo

After reboot you should be able to see all HD Audio components. 

```

$cat /proc/asound/devices

  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
  5: [ 0- 1]: hardware dependent
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 24: [ 0- 0]: digital audio capture
 33:        : timer

$
```

if this not help you, you can try

options snd-hda-intel model=dell-m42

See also: 
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Bye!

---

### Post by nicmar on 2008-06-10
YAY this worked for me!

---

### Post by hp3 on 2008-06-25
This solved all my problems, Vista is now out.
Thanx a lot !

---

### Post by Mudginho on 2008-08-01
I'm having the same issues with Gutsy 32bit on a U2E.  The sound fix for 8.04  works but alas the video fix doesn't seem to.  I'm fairly certain it's not a Xorg issue as manual editing of Xorg.conf produces some interesting results but no fix.

Any suggestions?

---

### Post by Mudginho on 2008-08-27
Perusing the X11 logs shows that there is a mysterious fourth display device (after the VGA & HDMI ports) called TV which creates a 1024x768 safe area.

xrandr --output TV --off

Kills this output and removes the safe area.

Unfortunately as is the way with X11, fiddling with Xorg.conf tends to result in a broken system.

---

