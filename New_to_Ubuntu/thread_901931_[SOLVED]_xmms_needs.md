---
title: "[SOLVED] xmms needs"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by mdecler2 on 2008-08-26
I compiled xmms from source with the following dependencies:
libogg-dev, libvorbis-dev, libgtk1.2-dev, and libalsa-dev.

This was my configure line:
./configure --prefix=/usr --with-ogg-prefix=/usr/lib --with-vorbis-prefix=/usr/lib --with-alsa-prefix=/usr/lib

But it says that the ALSA plugin will not be installed after configuring.
Where is ALSA, and how can I get xmms to work?

When I continued compilation anyway, XMMS would zip through the songs in my playlist with no sound whatsoever. I am guessing it doesn't have ALSA to back it up.

---

### Post by unutbu on 2008-08-26
Do you have libasound2-dev installed?

---

### Post by Nepherte on 2008-08-27
Why not install xmms from the repositories?
```
sudo apt-get install xmms2
```

---

### Post by mdecler2 on 2008-08-29
Maybe they call this necromancing, but I am cleaning up the mess I started!
If you are looking for a more up to date install of xmms (as of 8/29/08 ), then try this thread I started:
[http://ubuntuforums.org/showthread.php?t=901932](http://ubuntuforums.org/showthread.php?t=901932)

As many know Ubuntu Hardy Heron does not have xmms in the repos anymore. Don't worry! There are solutions. Good luck to you!

---

