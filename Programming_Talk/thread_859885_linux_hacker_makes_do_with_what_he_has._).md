---
title: "linux hacker makes do with what he has. :)"
date: 2008-07-15
forum: Programming Talk
---

### Post by slavik on 2008-07-15
so, you have a ps3 hooked up to your system via toslink (optical spdif). your ps3 is set to output audio in DTS format ... how do you decode it and play it back on the speakers?

NOTE: there are a few ways to do this, but this is the best one I can come up with:

arecord -D spdif -t raw -f S16_LE -r 48000 -c 2 | ffmpeg -f dts -i - -f s16le - | aplay -r 48000 -c 2 -f S16_LE

ffmpeg uses libdca (libdts is the older name of the library), unfortunately gstreamer is based on the old library and doesn't exactly work.

gstreamer pipeline would look something like this (I couldn't get this working) :

gst-launch alsasrc device=spdif ! audioconvert ! dtsdec ! audioconvert ! alsasink

---

### Post by LaRoza on 2008-07-15
Old news...

:-)

---

### Post by slavik on 2008-07-15
> **LaRoza said:**
> Old news...

:-)
I couldn't find anything on decoding dts or ac3 :( (only on encoding them) ...

needless to say, neither alsa nor gstreamer have a good way for decoding things ...

---

