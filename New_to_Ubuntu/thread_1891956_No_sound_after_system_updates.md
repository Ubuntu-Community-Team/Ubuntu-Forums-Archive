---
title: "No sound after system updates"
date: 2011-12-06
forum: New to Ubuntu
---

### Post by willsmithbelair on 2011-12-06
I'm on a fresh install of Ubuntu 11.10

My sound works perfectly until I download and install all the updates. Then I just get clicks and pops.

Should I just.. not install updates. :confused:

Also, how can I activate my middle mouse button acting as a scroll? Right now it does nothing, but on windows it shows an icon and I can drag my mouse down to scroll - You probably know what I'm talking about.

---

### Post by wildmanne39 on 2011-12-06
Hi, do you have pre-release updates enabled that will cause problems, that installs developmental packages.

Also you can install synaptic package manager and lock the sound package only from being updated, it is most likely called ALSA.
Thank you

---

### Post by willsmithbelair on 2011-12-07
> **wildmanne39 said:**
> Hi, do you have pre-release updates enabled that will cause problems, that installs developmental packages.

I doubt it. It's just the default update manager that pops up on a fresh install. It has "Security Updates" and "Recommended Updates" subsections. ([IMG]http://i41.tinypic.com/np15hi.png[/IMG]

> **wildmanne39 said:**
> 
Also you can install synaptic package manager and lock the sound package only from being updated, it is most likely called ALSA.


I can't seem to find where to do this from within synaptic. Also isn't there pulseaudio also? I'd have to lock all their dependencies as well would I not...

---

### Post by willsmithbelair on 2011-12-08
Correction, doesn't matter if I update or not since my sound just stopped working when I booted up this morning.

Works fine right after install, until I reboot my computer - then it fails.

$aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1828S Analog [VT1828S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1828S Digital [VT1828S Digital]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```0 is ATI SBx00 built in sound on a MSI 770-g45 motherboard
1 is HDMI from an ATI 5770

I can hear it click/pop in my headphones when I mute and unmute, but that's it.

my sound works fine with just alsa on my arch linux partition.. so this is an ubuntu problem with this hardware I guess or pulse.

---

### Post by wildmanne39 on 2011-12-08
Hi, you can have a look at this thread and see if it helps.
[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)
Thank you

---

