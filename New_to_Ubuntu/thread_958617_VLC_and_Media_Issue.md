---
title: "VLC and Media Issue"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by RussW210 on 2008-10-25
I made the big mistake of trying to open VLC Media Player with sudo/gksudo.  Now, every time I restart the computer it sets Deinterlacing on Discard and I can't seem to get it to stick.  Anybody have an idea how to get Discard to stay.  I go to Settings, Preferences, and change it there then save but as soon as I restart the computer it goes back to Discard.

---

### Post by kansasnoob on 2008-10-25
The only thing I can think of is to purge VLC entirely.

First of all go to Synaptic and search VLC, then make a note of all VLC you have installed. I use mozilla-plugin-vlc, vlc, and all vlc-plugin-***.

Then (at terminal) run:

```
sudo apt-get remove --purge vlc
```

Then go to Synaptic and reinstall all of the VLC packages you just purged.

That should give you a fresh VLC.

---

