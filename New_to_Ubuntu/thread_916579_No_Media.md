---
title: "No Media"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by sophtpaw on 2008-09-11
Hi,

i can not play any of my music or movie files. Totem comes up when i click on a media file, but nothing happens. So, i tried opening with Mplayer with the same result/experience. 
The files are good 100% so i am stumped.
I installed ubuntu extras for all the media codecs.

Any help suggestions gratefully received,

Thank You

---

### Post by skippuff54 on 2008-09-11
can u do anything on the web like youtube

---

### Post by SunnyRabbiera on 2008-09-11
are you running multiple audio apps at the same time?
are you using alsa?

---

### Post by sloggerkhan on 2008-09-11
Have you tried [http://www.medibuntu.org](http://www.medibuntu.org) ? 
What formats are you trying to play?
I have not met a format that could not be played by a proper install of smplayer/mplayer, though xine is better for DVDs.

---

### Post by sophtpaw on 2008-09-11
Everyone,

Thanks for your responses.

Yes, Youtube, Zattoo tv, Last.fm all worked, hence i was confounded having installed ubuntu extras with all the extra codecs for multimedia including java and flash.
The problem and the solution in the end was simple - Pulseaudio.
I went into System>Preference>Sound and switched from 'Autodetect' to 'Alsa' 
Now all my media files audio or .avi etc work again with Totem or Mplayer or whatever else.

Seems Pulseaudio didn't like my system :(

k, Thanks again One and All

---

