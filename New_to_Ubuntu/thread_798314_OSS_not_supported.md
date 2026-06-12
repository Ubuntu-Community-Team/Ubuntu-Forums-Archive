---
title: "OSS not supported?"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by DMinard on 2008-05-18
alright ive tried setting up wine on ubuntu hardy on different variants and i keep finding myself in a sound situation. when i launch winecfg i get some lines in my terminal that say:

 ~ $ winecfg
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.


as a result i cannot get any sound through wine. i would really like some sound in wine if someone could help plz

---

### Post by ajmorris on 2008-05-18
hi there,
try running winecfg and going to the audio tab, and selecting alsa. Then click test sound, and post any errors here if you do not hear a sound from clicking that button.

AJ

---

