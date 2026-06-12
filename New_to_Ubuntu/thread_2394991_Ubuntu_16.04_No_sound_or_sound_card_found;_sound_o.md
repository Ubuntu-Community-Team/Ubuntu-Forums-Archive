---
title: "Ubuntu 16.04 No sound or sound card found; sound output showing as 'Dummy output'"
date: 2018-06-25
forum: New to Ubuntu
---

### Post by russ15 on 2018-06-25
Hi,

I know similar issues have been posted, but the fixes mentioned there do not seem to work or cover the issue I am experiencing.

I have had Ubuntu installed and running on this laptop for ~1 year with no issues. The other day the sound stopped working for everything other than headphones. While trying to fix that, I fear I have made it more of an issue. Now the sound does not work for anything, and there is only 'Dummy output' available as a sound output. The microphone also seems to not be working. 

Additionally, despite alsa being installed, alsamixer returns 'cannot open mixer: No such file or directory'.

I have tried purging and reinstalling alsa and pulseaudio to no avail.

sudo aplay -l
returns:
aplay: device_list:268: no soundcards found...


sudo lspci -v | grep -A7 -i "audio"

returns:
00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)
    Subsystem: CLEVO/KAPOK Computer Device 2410
    Flags: bus master, fast devsel, latency 32, IRQ 133
    Memory at df320000 (64-bit, non-prefetchable) [size=16K]
    Memory at df300000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [50] Power Management version 3
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: snd_hda_inte

Adding "options snd-hda-intel model=auto" to the [COLOR=#333333][FONT=UbuntuMono]alsa-base.conf[/FONT][/COLOR]   did not work either.

I would really like to not have to reinstall Ubuntu. Are there any suggestions?

[Solved]: see below.

---

### Post by russ15 on 2018-06-25
After updating to a newer kernel it was working. However, the newer kernel had other issues, but when I regressed back to the old kernel it all worked still.

---

