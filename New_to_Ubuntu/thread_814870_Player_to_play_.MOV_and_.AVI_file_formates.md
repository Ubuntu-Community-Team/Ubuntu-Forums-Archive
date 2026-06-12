---
title: "Player to play .MOV and .AVI file formates"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-01
Could any one suggest me a player which can play .mov and .avi extensions.

could any one tell me good player like vlc that can support variety of file formates.

Or did i want to install any special codecs

---

### Post by metasolaris on 2008-06-01
Yes, VLC!

Nothing better in my book!

meta

---

### Post by rraj.be on 2008-06-01
but in vlc when i played my .mov files its just running blank without any sound or picture.

should i install any specific codec?

---

### Post by sayakb on 2008-06-01
```
sudo apt-get install ubuntu-restricted-extras
```
This will install the necessary Gstreamer codecs.
After that, you shall be able to play them on the default movie player (Totem)

---

### Post by SunnyRabbiera on 2008-06-01
practically any video player in linux will play avi's and mov's once you get the proper codecs and stuff installed.
I personally prefer to use smplayer or xine.

---

### Post by tbzep on 2008-06-02
On a related note, I already have the extended package mentioned above on my system.  However, I still get an error when trying to play AVI files.

> The playback of this movie requires a video/x-avi-unknown decoder plugin which is not installed.

This file plays fine on WinBlows machines.

---

### Post by rraj.be on 2008-06-02
I installed that package but still i cant play .MOV files.

---

### Post by SunnyRabbiera on 2008-06-02
> **rraj.be said:**
> I installed that package but still i cant play .MOV files.

try the mediabuntu repositories too as sometimes gstreamer wont do it.
You can try to install the win32 codecs with it

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

