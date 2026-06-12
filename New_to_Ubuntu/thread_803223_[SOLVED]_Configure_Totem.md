---
title: "[SOLVED] Configure Totem"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by NaF on 2008-05-22
Isn't it possible to configure Totem more than what's in the preferences page? If it is, where can I do that?
I like totem much over VLC, namely because VLC flashes and did all kinda weird things when changing vidoes. But if I can't get Totem to auto-fullscreen and go to a aspect-ratio of 4:3 on load, I'll have to look for another alternative :(?

---

### Post by NaF on 2008-05-22
anyone :confused:?

---

### Post by NaF on 2008-05-24
> **NaF said:**
> Isn't it possible to configure Totem more than what's in the preferences page? If it is, where can I do that?
I like totem much over VLC, namely because VLC flashes and did all kinda weird things when changing vidoes. But if I can't get Totem to auto-fullscreen and go to a aspect-ratio of 4:3 on load, I'll have to look for another alternative :(?

In case someone else is trying to do this at some point, I got it working by calling the playlist: ```
 totem --fullscreen '/home/videos/playlist' 
``` and going into the terminal you can open up ```
 gconf-editor
``` browsing to ```
 /system/gstreamer/0.10/default/ 
```, and setting ```
 videosink 
``` to ```
 xvimagesink pixel-aspect-ratio=4/3 
``` will force totem to go into an aspectratio of 4:3. 

Alternatively, mplayer can be forced to do so by going into the ```
 /etc/mplayer/mplayer.conf 
``` and telling it to go fullscreen and what aspect-ratio you want. 

Hope you don't waste as much time on this, as I did ;)

---

