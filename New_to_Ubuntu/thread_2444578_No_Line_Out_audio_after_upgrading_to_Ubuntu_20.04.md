---
title: "No Line Out audio after upgrading to Ubuntu 20.04"
date: 2020-06-01
forum: New to Ubuntu
---

### Post by hillwalker801 on 2020-06-01
I have two dual booting desktops (Windows 10 and Ubuntu). Both use a Gigabyte GA-78LMT-USB3 motherboard. The Front Audio header of each motherboard is connected to an identical multimedia front panel.

The primary PC is connected to my HP w2207h monitor HDMI input via the GeForce GT730 graphics card. The motherboard audio Line Out is connected to an amplifier and speakers.

The secondary PC is connected to the same monitor VGA input via a Gigabyte GeForce 210 graphics card. The motherboard audio Line Out is connected to the monitor audio line input. 

The audio Line Out of both PCs functions correctly in Windows. As far as I can remember the audio Line Out of both PCs functioned correctly with Ubuntu 18.04. 

After recently upgrading to Ubuntu 20.04 I reinstalled WINE and Winamp, which had been giving problems under Ubuntu 18.04. The upgrade and installs all appeared to have completed successfully.

Trying to play audio tracks now using Winamp under Ubunto 20.04 I discovered that neither of the audio Line Out functions correctly. If I select the headphones using the Settings/ Sound/ Output Device I can hear the sound fine at the multimedia front panel. If I select HDMI output on my primary PC I can also hear the sound via my monitor. If I select Line Output there is no audio Line Out even though the blue dashes under the Output Device windows suggests an audio output is present.

I've had a look at the ALSA mixer and tried switching between channels there but still no audio Line out. I've also tried resetting the ALSA mixer, but still no audio Line Out.

Can anyone suggest how to get my audio Line Out to function correctly?

---

### Post by TheFu on 2020-06-01
Unplug the headphone-out. Wait 10 seconds.  Plug in the headphone-out.  Pulse audio likes to automatically switch to the most recent connection.

The GeForce 210 is well beyond End of Life, BTW.  I suspect the GeForce GT730 might be too.  My GeForce 7200 GS was since 16.04. In the end, I replaced it with the cheapest 1030 I could find.

With pulse audio, run the **pavucontrol** tool to control sinks and sources.

Line-out and speaker-out don't have the same levels. Levels for line-out is usually extremely low.

---

### Post by hillwalker801 on 2020-06-01
Thanks,

I unplugged the headset and used pavucontrol to select output to Line Out (plugged in). There is an indication of audio present in that the indicator bar is pulsing irregularly. Still no sound out of the monitor speakers though.

I appreciate the graphics cards are dated but they aren't broken (they still work perfectly well in Windows) and I'm not in the habit of replacing my hardware on a whim. The problem I'm having is with the audio Line Out from the motherboard to the monitor.

---

### Post by hillwalker801 on 2020-06-06
Problem still exists. Can anyone else suggest any other action to resolve it? What puzzles me is that the sound level indicator bar in Settings/Sound suggests sound is present at the Line Out - but nothing is getting to the monitor audio Line Input.

---

