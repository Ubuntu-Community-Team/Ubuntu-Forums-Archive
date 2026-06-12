---
title: "Streaming Videos"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by adobrakic on 2008-07-16
I have VLC installed, and VLC-stream or whatever its called for streaming videos online. It's absolutely buggy, though. It sometimes crashes my firefox, can't get out of full screen mode, doesn't go over screenlets, etc.

What video streamer for ubuntu is the best?

---

### Post by RomeReactor on 2008-07-16
Hi. Make sure you don't have multiple video plugins for Firefox, as it may cause conflicts.

Give the Mplayer plugin a try; close Firefox, open a terminal and run:
```
sudo aptitude purge mozilla-plugin-vlc totem-mozilla && sudo aptitude install mozilla-mplayer
```

---

### Post by AndyCooll on 2008-07-16
Folk often mention VLC and MPlayer. These are however unecessary. The default player (Totem) with the relevent codecs installed handles streaming video fine.

:cool:

---

