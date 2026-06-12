---
title: "no sound"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by someguy91 on 2008-10-30
I was having sound issues with VLC, and switched the output modules to ALSA; everything worked fine. Then a couple days after upgrading to Ibex beta, the sound died on me. This time, everything went. So I went into System > Preferences > Sound. Tried to test playback under ALSA, and this is what I get:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

I try autodetect.. this is what i get:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused

asoundconf list

gets me:

Names of available sound cards:
Intel

Any help would be appreciated.

---

### Post by lH)4~mK0e on 2008-10-31
As far as I know, you would have to switch everything to Autodetect in the Sound preferences (making it use pulseaudio).

---

