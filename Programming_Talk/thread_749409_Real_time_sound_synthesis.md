---
title: "Real time sound synthesis?"
date: 2008-04-08
forum: Programming Talk
---

### Post by jbm222 on 2008-04-08
I've been tossing around a few ideas to try to make a real-time synth program--that is, something that turns a PC into a synthesizer that can be played just like any other instrument, as opposed to a sequencer based synth.

Anyway, I don't really know where to start as far as what sound libraries to use.  For a rough first cut, I'd just like to be able to generate a tone and vary the frequency & volume in response to key strokes fast enough that the latency is unnoticeable.

I've done enough with GUIs that I don't need any help with the interface side, but can anyone give me some suggestions for the audio?

---

### Post by Zugzwang on 2008-04-08
The [JACK]("http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit") system is optimized for low-latency applications.

Maybe this advice is out-of-date: It's the best free audio system/library for Linux for low-latency stuff (so far).

---

