---
title: "ID3 tag demuxer missing?"
date: 2011-09-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rv65 on 2011-09-03
Due to the Gstreamer breakage, I can't seem to play MP3 files, since ID3 Tag demuxer is missing. Any plans on when to fix gstreamer? I want to play mp3's again.

---

### Post by mc4man on 2011-09-03
Both the gstreamer ugly & fluendo plugins are working fine here to provide mp3 decoding in gstreamer. You could try the fluendo one
```
sudo apt-get install gstreamer0.10-fluendo-mp3
```

---

### Post by rv65 on 2011-09-10
I still don't have ID3 demuxer, and I do have fluendo mp3.

---

### Post by rv65 on 2011-09-10
Now it has gotten even worse. Now I can't get any mp3 to work on any player. I have all the plugins, and it could be my X-Fi card.

---

### Post by dino99 on 2011-09-10
dont instal gstreamer0.10-pitfdll (purge it as it breaks readings)

---

### Post by rv65 on 2011-09-10
I don't see it in my gstreamer. I did remove the multiverse bad plugins

---

### Post by mc4man on 2011-09-10
> **rv65 said:**
> I don't see it in my gstreamer. I did remove the _multiverse bad plugins_
gstreamer mp3 decoding is supplied by the _ugly_ plugin and or fluendo (both can be installed but I believe gstreamer will default to fluendo if installed, just use the ugly here.
Have you tried a non-gstreamer player (audacious, mplayer, vlc, ect - though do beware of some vlc interface issues

I'd try creating a temp new user & see if that login can play mp3's in totem or banshee (or anything else

---

### Post by rv65 on 2011-09-18
I can play some files on banshee, but totem is borked. Alsaplayer can play certain MP3's. It could some tagging issue, and I must have some kind of conflict.

---

### Post by rv65 on 2011-09-18
I also have the oneiric medibuntu repistory enabled as well.

---

