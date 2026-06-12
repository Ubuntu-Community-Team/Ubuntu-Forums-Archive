---
title: "Sound Blaster Live and AC97 Audio"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by moolcool on 2008-08-01
Bizzare! I have a Sound Blaster Live! in my computer along with on board AC97. I can only get sound out of the SoundBlaster from Pidgin and Firefox, Nothing from VLC or Amarok, they wont even play OGG Files, and I already got that restricted files package. The weirdest part is that it does play all audio in KDE.

---

### Post by oliviacond on 2008-08-02
switch to ALSA (System->Preferences->Sound).
make sure firefox is closed if u wanna use vlc.

---

### Post by Ryadt on 2008-08-02
> **oliviacond said:**
> make sure firefox is closed if u wanna use vlc.

You can use firefox and vlc together if you end pulse audio```
killall pulseaudio
```:)

---

