---
title: "Multiple audio video issues (flash and XBMC)"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by Gr3y on 2008-07-13
I have system sound, but no sound in flash. Also my videos in XBMC play in fast motion with no sound. 

I have installed the flash plugin, the support library, and alsa-oss.
When I start Firefox from konsole and try to play a flash video it throws the following:
[code]
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
[code]

Video's and MP3s work fine in dragonplayer, just not in my actuall media center software.

Also: Kmix wants to default my output through the HDMI connection on my videocard, I manually set it to the motherboard and PCM for the primary master. I've manually set Kcontrol to use ALSA as the sound manager but I still have no sound in flash.

---

### Post by Gr3y on 2008-07-14
Running alsamixer in Konsole shows that the HDMI port on my videocard is the selected sound card. However I would think that would mean that I wouldn't have system sound.

I'm running kubuntu so I shouldn't have to worry about pulseaudio, is there a simple way to configure alsa to only look at my onboard sound?

---

### Post by Gr3y on 2008-07-14
Okay I've isolated the problem. When I run asound -l I see three sound devices, the HDMI on the videocard (which is what's being used as the default on ALSA), the soundcard on my motherboard (which is what I want to use), and then what I think is my modem.

I was screwing around with the alsa config last night and for a second had it working, sound in flash and proper media behavior in XBMC, however after a reboot it stopped working again.

I'll post the outputs of everything tonight, but can someone please post a link on how to remove a sound device from alsa? I tried setting the onboard sound with an index of 0 but that doesn't seem to work.

Also how do I restart alsa without rebooting?

Thanks.

---

