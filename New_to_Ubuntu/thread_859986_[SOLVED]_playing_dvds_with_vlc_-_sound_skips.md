---
title: "[SOLVED] playing dvds with vlc - sound skips"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by darkline on 2008-07-15
When i play a dvd with vlc, the sound frequently skips slightly.
This is ofc incredibly annoying and completely stops me watching the film.

When the dvd is being played my cpu usage is about 50% and i see no errors in the terminal.

I have also tried playing this dvd in totem and for some reason the language there is german, and it seems impossible to change it (when i click on languages>english nothing changes (and it was already selected) nothing happens when i select auto and when i select german it goes silent.


Has anyone got any ideas how to solve either problem?

Thanks

---

### Post by darkline on 2008-07-15
I think i have (kinda) solved this myself.

Changing vlc to output with alsa rather than pulseaudio gets rid of the skipping sound.

Still not sure why pulseaudio skips though, but the workaround is fine for me, as it is only with dvds

---

