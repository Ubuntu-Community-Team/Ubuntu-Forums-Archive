---
title: "Cannot record with microphone in Hardy Heron"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by jayssite on 2008-04-28
I'm not able to record with my microphone on Ubuntu 8.04. When I try to record audio with Sound Recorder, using either my front or rear mic port, I hear nothing when I try to play it back. (Audio plays fine when I load other files in it, though.)

I'm not sure what information is helpful, so here's what I can think of:
I have a Dell XPS 410. The set up of audio ports is as follows:
front: mic, headphones
rear: mic, speakers, surround side speakers, subwoofer, line in

These are the options in Sound Recorder's "Record from input" dropdown: IEC958, Capture, Capture 1, Capture 2, Digital, Mux, Mux 1, Mux 2. (I have no idea what any of those mean.)
In Volume Control, these are the options in File -> Change Device:
- HDA Intel (Alsa Mixer)
- SigmaTel STAC9227
- Playback: ALSA PCM on front:0 (STAC92xx Analog) via DMA (PulseAudio Mixer)
- Capture: Monitor Source of ALSA PCM on front:0 (STAC92xx Analog) via DMA (PulseAudio Mixer)
- ALSA PCM on front:0 (STAC92xx Analog) via DMA (PulseAudio Mixer)


So, is there something I've neglected to do? Or might this be a bug?
Maybe Ubuntu is somehow confused by the multiple mic ports?

---

### Post by jayssite on 2008-04-29
After spending a while on Google, I have figured this out.
If anyone else is having this problem, it turns out you have to go into Volume Control, Edit -> Preferences, select the "Input Source" checkbox, go to the "Options" tab that has newly appeared, and finally choose the appropriate input source.

Far from "just working" like Windows would, though. And when the audio is played back, it only comes from the left speaker, but I don't know if that's the fault of Ubuntu or Sound Recorder.

---

### Post by ironwolfe on 2008-04-29
I am not sure this still works in Hardy, but ALSA is best adjusted from the command line - paste this into the terminal (under App -> Accessories -> terminal

```
alsamixer
```

hit TAB to go to the capture settings - hit TAB again for ALL settings (play/capture).

use the "m" key to toggle a feature on or off.  

I am not sure if this still works with Pulse Audio though - I imagine it is still there in the background.

---

### Post by randytuggle on 2008-05-01
I've tried everything on my Acer laptop and recording with a mic never works right. The best I can get is a very low level recorded input - or something that is not only low volume - but sounds distorted,too. I've used sound recorder and Audacity. I'm familiar with Audacity, as I have used it for years on various computers. What is up with this recording issue?

---

