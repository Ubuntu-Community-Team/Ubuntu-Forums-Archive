---
title: "gnash, ffmpeg, and gstreamer for FLV"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by fontenot_1031 on 2008-05-07
I've gotten gnash installed by
```
sudo apt-get install mozilla-plugin-gnash
```
which has worked for most flash files except for youtube videos.  I heard that you need to install gstreamer and ffmpeg for those to work.  Does anyone know how to install gstreamer and ffmpeg so that they can work with gnash?

---

### Post by tjwoosta on 2008-05-07
sry i dont actually know what gstreamer and ffmpeg are but i do know that flashplugin-nonfree works great for me with youtube and all other flash sites

if you wanted to install it this is what you do

first remove gnash
```

sudo apt-get purge mozilla-plugin-gnash

```
then install flashplayer-nonfree
```

sudo apt-get install flashplugin-nonfree

```

by the way nonfree means its not opensource, it doesn't mean you have to pay

---

### Post by fontenot_1031 on 2008-05-07
> **tjwoosta said:**
> by the way nonfree means its not opensource, it doesn't mean you have to pay
I want to support the gnash project by using their plugin.  I have used the non open source one before though.  So I don't completely object to using it.

---

### Post by tjwoosta on 2008-05-07
ahh.. i see

well actually  i was just trying to figure out how to help you so i uninstalled flashplugin-nonfree and installed gnash (i checked and i already had gstreamer installed so i installed ffmpeg)

i went to youtube and it does work but then i tried stumble-upon and i stumbled a couple of videos and it didnt like that very much, only the first two that i tried actually played

but like i said, for some reason i already had gstreamer and then i just installed ffmpeg in synaptic (medibuntu repository)

---

