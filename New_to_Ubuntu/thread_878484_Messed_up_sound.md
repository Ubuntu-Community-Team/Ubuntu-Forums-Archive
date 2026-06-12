---
title: "Messed up sound"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by JaimeZX on 2008-08-02
Hi gang. As usual, I am a total n00b to Linux. Well, actually I installed Red Hat on an old laptop YEARS ago but it was rained on shortly thereafter so my experience is VERY limited.

Anyway. I put a new mobo/CPU combo in my machine (Asus M2A-VM & AMD Athlon 64 5000+) and decided to ditch Windows while I was at it.

Runs great! Plenty fast! But. The audio is totally jacked up. The Asus has onboard sound which I *think* I've deactivated, but I can't be sure because neither the manual nor the BIOS menus specifically have something like "ON-BOARD SOUND [_] Enable [_] Disable."  So I took my best guess.

Anyway. I have a Sound Blaster Audigy MP3+ that I acquired back in 2003. Great card.

I can HEAR all the sounds, but they're very distorted as though the speakers were all blown out or the volume was cranked way up. Except they're not and it's not. I turned on every volume control I could find and set them at about 20% and the thing still sounds distorted.

In Sound Preferences all of the options are set to "ALDA" and the device is "Audigy1." 

I have searched these forums and tried a whole bunch of things suggested but none have worked; perhaps because most of them involved fixes for using on-board sound and many featured something along the lines of "guess I might need to go buy a sound card."

I'm sorry I can't anticipate y'all's questions but I've been using Microsoft OSes since the heady days of DOS 6.0 and am much better at troubleshooting those. If I can't get this sound fixed I may need to go back that way. :/

Thanks in advance!

Jim

---

### Post by northern lights on 2008-08-04
Can you please post the output of ```
sudo lshw -C multimedia
``` and ```
cat /proc/asound/cards
```

Thank you.

---

### Post by bobnutfield on 2008-08-04
Your sound card is generally supported out of the box with ALSA.  If you are getting sound of any kind, the card is working, but it does sound as though the onboard sound may be getting some resources.

It may not have any effect, but try in a terminal:

> sudo /etc/init.d/alsa-utils reset

---

### Post by JaimeZX on 2008-08-05
> **northern lights said:**
> Can you please post the output of ```
sudo lshw -C multimedia
```
```
  *-multimedia            
       description: Multimedia audio controller
       product: SB Audigy
       vendor: Creative Labs
       physical id: 6
       bus info: pci@0000:02:06.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2 module=snd_emu10k1

```

> and ```
cat /proc/asound/cards
```

Thank you.

```
 0 [Audigy         ]: Audigy - Audigy 1 [SB0090]
                      Audigy 1 [SB0090] (rev.3, serial:0x511102) at 0xc800, irq 21

```


> Your sound card is generally supported out of the box with ALSA. If you are getting sound of any kind, the card is working, but it does sound as though the onboard sound may be getting some resources.

It may not have any effect, but try in a terminal:

Quote:
sudo /etc/init.d/alsa-utils reset 

I'm pretty sure I disabled the on-board sound in BIOS. I tried your reset but it had no effect on the audio quality.

Also, today the update thing was flashing on the taskbar so I looked at the available update and it said it was some kind of ALSA update. So I figured "what the heck, it can't make things worse..."

Anyway. Now if in Sound Preferences I choose "ALSA" from the list for any of the (Effects/Movies,etc) and click "TEST" it gives me the error
```
audiotestsrc wave=sin freq=512 ! 
audioconvert ! audioresample ! gconfaudiosink:
Could not open audio device for playback.
```

I can choose any of the other options to hear the sample (or any sound) in the poor, distorted, scratchy version. 

So. :dunno:

As always, advice is most welcome, and thanks for the replies so far! :)

---

### Post by northern lights on 2008-08-06
> **bobnutfield said:**
> Your sound card is generally supported out of the box with ALSA.  If you are getting sound of any kind, the card is working.
This part is not only true, but also confirmed by the outputs you posted. Those also confirm the onboard being disbled. 

Can you verify this is not a hardware issue and equalizer settings are not through the roof?

---

### Post by JaimeZX on 2008-08-06
> **northern lights said:**
> This part is not only true, but also confirmed by the outputs you posted. Those also confirm the onboard being disbled. 

Can you verify this is not a hardware issue and equalizer settings are not through the roof?

Equalizer settings are all at about 20%.

The sound card worked fine on my machine before, but I have changed out my mobo/CPU. I suppose there could be an issue with that combination; I haven't installed WXP on this machine since the rebuild so I can't say for sure that it works in Windows, only that it worked in Windows on my old motherboard.

---

### Post by northern lights on 2008-08-06
While for the sake of Ubuntu compatibility I'd like to see it be your board, I highly doubt it.

Any board should be able to deal with any commen sound card, or PCI device for that matter.

---

