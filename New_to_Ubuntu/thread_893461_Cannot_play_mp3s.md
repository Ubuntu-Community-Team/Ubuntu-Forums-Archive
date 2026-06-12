---
title: "Cannot play mp3s"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by sayakb on 2008-08-18
I installed kubuntu-kde4-desktop and amarok (kde3) on an Ubuntu Hardy amd64 installation. I used Exaile for my music collection. When trying to play mp3s using Amarok in KDE4, it shows: [I]Xine: Cannot play audio. Resource busy.
[/I]If I play anything in exaile, the program just freezes.
I tried Banshee, but it just shows a red cross on the song name and shows *unknown error.*

VLC plays the mp3s okay but I don't have an option to build a library there. 
What could be the problem?

---

### Post by billgoldberg on 2008-08-18
> **LinuxIsInnovation said:**
> I installed kubuntu-kde4-desktop and amarok (kde3) on an Ubuntu Hardy amd64 installation. I used Exaile for my music collection. When trying to play mp3s using Amarok in KDE4, it shows: [I]Xine: Cannot play audio. Resource busy.
[/I]If I play anything in exaile, the program just freezes.
I tried Banshee, but it just shows a red cross on the song name and shows *unknown error.*

VLC plays the mp3s okay but I don't have an option to build a library there. 
What could be the problem?

Don't reall know, but you could use the gstreamer plugins instead of xine and see if that will work.

---

### Post by sayakb on 2008-08-18
Maybe it *is* a gstreamer problem.. totem (gstreamer) shows up *Invalid argument: cannot connect to stream*. How do I install gstreamer backend for kde4? I have restricted extras installed for both kubuntu and ubuntu.

---

