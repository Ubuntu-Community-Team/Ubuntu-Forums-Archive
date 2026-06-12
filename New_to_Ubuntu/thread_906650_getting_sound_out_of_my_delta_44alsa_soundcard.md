---
title: "getting sound out of my delta 44/alsa soundcard"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by carpeme on 2008-08-31
I've got an AMD64 machine with a M-audio Delta 44 soundcard. Last time I had installed linux, they didn't have drivers for 32-bit let alone 64-bit, so I'm impressed.

The problem is, I'm a total noob and I can't get sound. Everything seems to be installed correctly, I don't see any error messages, but when I play an mp3, I don't hear anything from the speakers.

I installed envy24control and turned up the sound for hardware inputs 1 and 2, and routed hardware outs to the digital mixer, so now I can get sound from external devices. But for playing wav files etc, the volume's turned up, but I can't hear anything, and I don't see anything in the envy24control either. I also installed alsamixer/alsamixergui and turned up everything that I can, but I still don't hear anything.

My guess is that audio software is routing sound to a different device or a different track, but I haven't been able to find the right track. In Volume Control Prefences, I have it set to "M Audio Delta 44 (Alsa mixer)", track "Multi".

---

### Post by steve_q on 2008-11-27
Bump.

Precisely the same issue.  (32bit, however.)

I'm assuming the onboard soundcard (I82801DBICH4) is interfering somehow.

I've already tried disabling the onboard card in the BIOS.. when I do, my media player apps (Rhythmbox, Totem) stop responding upon load of any media file (mp3, flac, etc).

Thanks in advance!  :)

---

### Post by markbuntu on 2008-11-27
The most likely problem is that those apps are using the pulseaudio sound server which is misconfigured. There is an extensive guide to sound troubleshooting and setup here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Since you have an m-audio card, I assume you might be wanting to be doing some audio production work. There is also a jack section in the guide for that.

---

### Post by steve_q on 2008-11-28
Thanks for the link... but see next post please.

---

### Post by steve_q on 2008-11-28
After following the most lengthy process of reading/following the tutorial tree you provided, I had no results and lots of clutter.

I'm currently using a clean install of Ibex.

After going into my BIOS and disabling the onboard sound, I've actually heard SOMETHING.  (Bongo sound at login screen.)
**I don't want to use two cards**... just the M-Audio card.  It seems that Pulse is a way for Linux to use multiple cards in concert...


My new, but related question is:
Why would I not be able to play sound when my current recognized audio devices are as such?

**Results of: aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: M44 [M Audio Delta 44], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**Visible audio devices when I run: lspci -v**
02:02.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
        Subsystem: VIA Technologies Inc. Device d633
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at dce0 [size=32]
        I/O ports at dcc0 [size=16]
        I/O ports at dca0 [size=16]
        I/O ports at dc40 [size=64]
        Capabilities: <access denied>
        Kernel driver in use: ICE1712
        Kernel modules: snd-ice1712

**Results of: cat /proc/asound/modules**
 0 snd_ice1712

Is there any more info you'd need to guide me in changing files like  /etc/modprobe.d/alsa-base, and other necessary changes?  (the current error message I'm getting from RhythmBox when I try to play files of various formats is "couldn't get/set settings from/on resource."
--  My sound devices (/preferences/sound) have all been tried.  Using Autodetect hangs the sound mgmt app.

---

### Post by steve_q on 2008-11-28
This is the ugliest fix, but IT WORKED...  found it at [LaunchPad]("https://bugs.launchpad.net/pulseaudio/+bug/276582/comments/5") 
[https://bugs.launchpad.net/pulseaudio/+bug/276582/comments/5](https://bugs.launchpad.net/pulseaudio/+bug/276582/comments/5)

System/Preferences/Sound
- Set all to ALSA

EVERY TIME YOU BOOT:
Open up Terminal.
Type:
```
killall pulseaudio
```Sure wish Pulse wasn't mandatory in 8.04+ versions if it's so finicky...

Selah.

Thanks for the help anyway, Mark.  :)

---

