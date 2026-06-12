---
title: "Recording line in questions"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by editheraven on 2012-02-04
I have plugged an incoming audio connection in the microphone jack (the pink one, i guess). Anyway, the sound applet from pulseaudio (i think) can't set the boost and the sound is too low. In alsa-mixer, the one with gui, i can set the volume and boost for the microphone and everything is going well.


Anyway, in audacity/arecord etc i can't figure it out to what device is the application listening to. In other words, from what device i must record? alsa/pulseaudio? How do i figure it out?

---

### Post by ajgreeny on 2012-02-04
Run ```
alsamixer
``` in terminal and check that the levels of outputs are not set too low.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will take you from "playback" to "capture" and in capture you can move to "Line" and hit spacebar to enable the line-in capture.
Esc will save and exit.

---

