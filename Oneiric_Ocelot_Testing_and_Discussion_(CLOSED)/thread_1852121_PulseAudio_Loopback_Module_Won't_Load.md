---
title: "PulseAudio Loopback Module Won't Load"
date: 2011-09-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Sam Lars on 2011-09-29
I just upgraded to Oneiric and have been getting used to the changes...
Before, to let sound from the mic play through speakers, I would run:
```
pactl load-module module-loopback
```
And it would then work. It would have an annoying lag, but it would work.
I tried the same thing in Oneiric and it failed:
```
~$ pactl load-module module-loopback
Failure: Module initalization failed
```
I ran
```
pacat -r --latency-msec=1 -d  alsa_input.pci-0000_00_1b.0.analog-stereo | pacat -p --latency-msec=1 -d  alsa_output.pci-0000_00_1b.0.analog-stereo
```
From [this post]("http://ubuntuforums.org/showpost.php?p=10596256&postcount=11"), and that made it work...
Anyone know what changed or why this won't work?

---

### Post by thatguruguy on 2011-09-29
Check your pulseaudio version. A change made in Pulseaudio 1.0 is that it now supports passthrough.

---

### Post by Sam Lars on 2011-09-29
I have 1.0, so does that mean you don't have to load that module anymore?

---

### Post by thatguruguy on 2011-09-29
I don't know, because I haven't tried it.

Try it, and let us all know how it works.

---

### Post by Sam Lars on 2011-09-29
Well I don't get any loopback until I run that command.
But after running that command, pulseaudio suddenly uses a lot of CPU. It was at 18-19% on my 1.86 GHz Core 2 Duo. I changed the resample to "trivial" in the configuration file and in went down to 14-15%. I remember it being half that before the upgrade. Also, evidently from that command, pacat is using an additional 8%.

---

