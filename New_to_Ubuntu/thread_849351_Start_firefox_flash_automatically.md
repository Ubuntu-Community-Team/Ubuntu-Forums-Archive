---
title: "Start firefox flash automatically"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by brownknight on 2008-07-04
Hi. I am running Xubuntu 8.04. I did a clean install since Ubuntu 8.04 seems to slow down my laptop compared to previous Ubuntu releases (Acer Travelmate C110). 

Anyway, when I open up firefox, and watch a video (youtube), the movie does not automatically start. It has this big grey arrow in the middle of the black screen. I have to click on  this before the flashmovie starts. This is the same for all flashmovies on firefox and not youtube alone. 

My question is how do I make this feature go away. I want the flash to start playing when I go to a page with movie on it and not click on it before it starts. Thanks for taking time to read this.

---

### Post by tjwoosta on 2008-07-04
the flashplayer that you are describing sounds like what happened to me when i was using the swfdec player

to make it work better and autoplay uninstall the swfdec player (or whatever flash you have)

then install the regular adobe flash (flashplayer-nonfree)

to remove swfdec player (if thats what you are infact using)
```
sudo apt-get purge swfdec-mozilla
```

to install flashplugin-nonfree
```
sudo apt-get install flashplugin-nonfree
```

---

