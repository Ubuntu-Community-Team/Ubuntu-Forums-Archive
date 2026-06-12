---
title: "[SOLVED] Rhythmbox doesn't work"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by subaruwrc01 on 2008-06-17
I'm currently using Ubuntu 8.04.  Rhythmbox won't play any type of file. You click play on a song and nothing happens.  I have all the necessary codecs.

---

### Post by sdennie on 2008-06-17
Someone else had a similar problem earlier and they were able to fix it by going to System->Preferences->Sound and changing the output values there.  They didn't state if it was ALSA or PulseAudio that worked for them but, it's easy enough to try both.

---

### Post by subaruwrc01 on 2008-06-17
> **vor said:**
> Someone else had a similar problem earlier and they were able to fix it by going to System->Preferences->Sound and changing the output values there.  They didn't state if it was ALSA or PulseAudio that worked for them but, it's easy enough to try both.

It's not an issue of no sound, it's an issue of Rhytmbox not doing anything.

---

### Post by sdennie on 2008-06-17
Right.  Are you hitting play and it just sits there at 0:00?  That's the exact problem someone else was having and changing the sound output fixed it.  Presumably if Rythmbox doesn't know where to send its sound, it's just stalling.

---

### Post by subaruwrc01 on 2008-06-17
> **vor said:**
> Right.  Are you hitting play and it just sits there at 0:00?  That's the exact problem someone else was having and changing the sound output fixed it.  Presumably if Rythmbox doesn't know where to send its sound, it's just stalling.

Yeah.  Changing the sound fixed it.  Very odd.

---

