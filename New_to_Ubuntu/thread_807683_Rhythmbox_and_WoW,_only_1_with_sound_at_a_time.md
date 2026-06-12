---
title: "Rhythmbox and WoW, only 1 with sound at a time?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Rusty023 on 2008-05-26
Well, I'm trying to play my music from Rhythmbox while listening to the sound from World of Warcraft on Ubuntu 8.04, but when I start WoW first and then open Rhythmbox, songs won't play. It's not just the sound, the progress bar stays at 0:00. Any ideas?

---

### Post by T-Virus on 2008-05-26
Some sound drivers allow only one program to use sound card at the moment. I would say it's OSS, so you should change into ALSA. Well eh, just wait for a better reply. :)

---

### Post by thumper13 on 2008-05-26
> **T-Virus said:**
> Some sound drivers allow only one program to use sound card at the moment. I would say it's OSS, so you should change into ALSA. Well eh, just wait for a better reply. :)

 /agree, it's most likely OSS. My computer has the same issue. OSS will only allow you to play one thing at a time through your soundcard. ALSA will allow several.

To switch to alsa, open your Wine configuration, and it's under the sound tab, i believe. Just MAKE SURE that you uncheck OSS before checking ALSA, or you will have no sound at all.

---

