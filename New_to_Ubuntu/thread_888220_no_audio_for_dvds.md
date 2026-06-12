---
title: "no audio for dvds"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by WinterMadness on 2008-08-12
sudo aptitude install libdvdnav4 libdvdplay0 libdvdread3 libdvdcss2
tried that, and i installed gstreamer and such 

some of the above errored i dont remember which ones
i can get the dvd to play with vlc and xine, but no audio.

in vlc im only able to get one audio track, usually theres more
in xine it says audio is being used by something else

---

### Post by SunnyRabbiera on 2008-08-12
arou you sure you got all your volumes turned up?
are you using alsa as your sound system?

---

### Post by WinterMadness on 2008-08-12
> **SunnyRabbiera said:**
> arou you sure you got all your volumes turned up?
are you using alsa as your sound system?

yeah and its just dvds that dont do sound, everything else is fine

---

### Post by WinterMadness on 2008-08-12
actually, i figured it out. i had to switch alsamixer to digital and it was on analog. thanks for helping though

---

