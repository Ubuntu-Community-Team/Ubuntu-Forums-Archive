---
title: "Pimp your video player, install aaxine!"
date: 2006-05-18
forum: Outdated Tutorials &amp; Tips
---

### Post by glotz on 2006-05-18
aaxine - an ASCII art video player

I'm on Ubuntu, this might be slightly different on Kubuntu or Xubuntu, dunno. If this works also on (K/X)ubuntu, please post a reply.

Open synaptic package manager, search for xine-ui (3,5 MB) and install it. It couldn't find that one library out of the box, so I came up with this solution. I don't know if this can cause any problems, at least I've seen none so far. ```
sudo cp /usr/lib/libX11.so.6 /usr/lib/libX11.so
```
Then in terminal type aaxine [filename] to invoke your kewl new player! :cool:

---

### Post by Greeface on 2006-05-19
Nice.  Mplayer also does this if you type ```
mplayer [filename] -vo aa
```

---

### Post by doclivingston on 2006-05-20
And GStreamer apps (e.g. Totem) can too if you set the default video sink to "aasink" or "caca" (colour)

---

