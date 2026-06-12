---
title: "NVidia MCP51 sound not working"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by Happypants on 2008-11-21
Howdy folks! 

I've recently put Hardy on my desktop and finally got the video working properly (curses nVidia, curses!), but I'm still having some problems with the sound.  

The sound card isn't supported by ALSA, so I'm curious if there is a potential work around or an alternative mixer I could use cuz I kinda got used to being able to hear stuff.  

When I go into "Sound Preferences" and switch from Alsa to "USB Audio" I can get the test sounds to work, but that's as far as she goes.  

Here are the results I have from the lspci and the aplay if they're of help to anyone.

```
#lspci -v 
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 6020
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at fe028000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

```
# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [Microsoft Digital Sound System ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Any tips would be appreciated.  I'll keep struggling through it of course and let you guys know if I get any good results.

If anyone has an idea but needs more info then just let me know.  

P.S. It's an old Gateway GT5228 with a built-in motherboard card btw.

P.P.S. If this is in the wrong board, my bad... I'm new here. ;)

Almost forgot.  When I start up the mixer I get this little hello from my comp.

```
#gnome-alsamixer
** (gnome-alsamixer:6541): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Input Source"!

** (gnome-alsamixer:6541): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Input Source"!

```

Guess my comp and I are in the same boat on that one.

---

