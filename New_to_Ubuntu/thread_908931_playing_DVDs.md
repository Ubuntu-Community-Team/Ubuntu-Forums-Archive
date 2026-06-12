---
title: "playing DVDs"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by Andrew79 on 2008-09-03
Totem does not play DVDs? It searched for a sutible codec, and installed gstreamer. still no dvds?

---

### Post by kaibob on 2008-09-03
Lots of options--one is to install totem-xine and libdvdcss2 from the repo's. 

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

I assume you are talking about commercial, copy-protected DVD's.

---

### Post by tuxxy on 2008-09-03
Have you isntalled any codecs to enable DVD playback yet?

A good package is ubuntu-restrcited-extras , this will enable DVD, MP3 playback etc

If you just want the DVD working install libdvdcss2

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Tatty on 2008-09-03
[https://help.ubuntu.com/community/Multimedia](https://help.ubuntu.com/community/Multimedia)

Have a read through this page, it should sort you out. :)

---

### Post by Andrew79 on 2008-09-03
okay, i have downloaded everything that everyone suggested. no avail. any other suggestions on getting dvds to play?

---

### Post by Tatty on 2008-09-03
Well, whats going wrong?  Any error messages?

Have you installed libdvdcss2 from the medibuntu repo?

---

### Post by tuxxy on 2008-09-03
What are you plaing the DVD through, I recommend trying VLC which you can download from the repos, it will play virtually any file you care to throw at it

---

### Post by Andrew79 on 2008-09-03
okay, so i downloaded vlc. now what? all it has is a small box, no video. also, when i try to play the dvd through totem, it goes gray, and i have to force quit it.

---

### Post by tuxxy on 2008-09-03
What codecs have you installed, to play standard format DVD's, all you need is these packages **libdvdcss2** and **win32codecs**

---

### Post by nvikram on 2008-09-03
Like you, I downloaded everything and then when I tried to play, it turned out all jaggedy and pixely. The solution...

```
sudo apt-get install mpg123
```

---

### Post by Andrew79 on 2008-09-03
okay, i have downloaded EVERYTHING in this post that every one has suggested. vlc looks like a crap half project, there is no picture, just controls that do nothing. totem either goes gray or tells me it cannot read from the resourse.
any other choices? i want a media play just like windows media player. this is one thing that i do not want to be messing around with like this, i want it to just work. any better choices out here?
by the way, i apperciate everyones input and help on this

---

### Post by tuxxy on 2008-09-03
VLC is one excellent player

---

### Post by Andrew79 on 2008-09-03
one more thing, now my favorite video website is not working. it was before adding all these downloads, now nothing

---

### Post by Andrew79 on 2008-09-03
> **tuxxy said:**
> VLC is one excellent player

then how does it work? when i open it, all I see is just a set of controls

---

### Post by mc4man on 2008-09-03
> then how does it work? when i open it, all I see is just a set of controls

Without getting into setting vlc up as default (auto play) what about going (in vlc's upper panel)  **file** -> open disk (for dvd disk in drive.
Or for an .iso,  file -> open file, or for a folder (video_ts, ect.), file -> open directory

---

