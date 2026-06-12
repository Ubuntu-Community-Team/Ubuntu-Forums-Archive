---
title: "Back again, more sound issues"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by zeroxb on 2008-09-01
Earlier today I was experiencing problems with my sound after my first installation of Ubuntu. No sound played at all and eventually I fixed it by uninstalling my alsa drivers, reinstalling them, then rebooting. Now my system sounds work (login sound,ect), however none of applications produce sound (songbird, rhythmbox, ect). I've followed the instructions from this thread-

```
http://ubuntuforums.org/showthread.php?t=504379
```

but receive a message saying

"No candidate version found for libxine-extracodecs"

and

"No candidate version found for w32codecs"

after attempting to install.


Any ideas?

---

### Post by halitech on 2008-09-01
did you enable the multiverse in synaptic?

---

### Post by zeroxb on 2008-09-01
I'm not sure how to do that. I've only been using Ubuntu for a day :/

---

### Post by halitech on 2008-09-01
good screenshots and step by step instructions here

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by zeroxb on 2008-09-01
Excellent step by step tutorial, thank you. w32codecs installed, but gstreamer did not. Sound still does not play in songbird, rhythmbox, ect.

---

### Post by halitech on 2008-09-01
I think you need all the gstreamer plugins. Just open synaptic (System - Administration - Synaptic Package manager) and do a search on gstreamer and install them

---

