---
title: "Vimeo no go"
date: 2014-05-30
forum: New to Ubuntu
---

### Post by Hadaka on 2014-05-30
Ubuntu 12.04  What is needed to be able to view Vimeo files?
ubuntu restricted extras and the gstream set are currently loaded
but Vimeo files fail to play. Other type vids play fine, as do dvd's.
:$ firefox -v
Mozilla Firefox 29.0
I would prefer not to load chrome.
All the searching i have done i doubt this is going to happen..
thanks for any suggestions on this.

---

### Post by hacksonfive on 2014-05-30
What do you mean by "gstream[er] set"? Exactly what packages having to do with gstreamer do you have installed? 

From [here]("http://vimeo.com/forums/topic:113083"):
> In order to play Vimeo videos on Ubuntu (and some other Linux operating systems), you will need the following packages:

Firefox: 
gstreamer0.10-plugins-good 
gstreamer0.10-ffmpeg

Are you sure you have both of those installed?

---

### Post by monkeybrain20122 on 2014-05-30
Vimeo uses html5 and h264, so you would need gstreamer0.10-ffmpeg.

---

### Post by Hadaka on 2014-05-30
Hi, I had all 4 GStreamer pluggins , so i decided to bounce them,
one of them failed on the reload because of broken packages. so
after a little wine and sweet talk the packages were repaired and
all is well. Thanks for the help !

---

