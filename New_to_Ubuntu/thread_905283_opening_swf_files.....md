---
title: "opening swf files...."
date: 2008-08-30
forum: New to Ubuntu
---

### Post by ettercap on 2008-08-30
hello every1....

does any 1 know how to play .swf files.......

i want to play them in totem....i justwanna know wat packages(codecs...) to are be installed...

i've tried both klash & gnash ..they both $**k....

plz help...

---

### Post by ChildOfMana on 2008-08-30
Try installing the Gstreamer plugins (available from the repos). I'm pretty sure there's a Gstreamer plugin that adds support for .swf

I could be wrong though.

You could also try installing VLC Media Player from the repos as I *think* that will play .swf files too.

---

### Post by airtonix on 2008-08-30
swf files that are meant to be videos are actually '.flv' files. 

swf files that are not meant to be videos, will only play in firefox as far as i am aware.

in any case, drag and drop onto firefox...

---

### Post by MasterSander on 2008-08-30
yeah swf only plays in firefox, you could try to write a html page for it, or try drag and drop as airtonix suggested

---

### Post by sayakb on 2008-08-30
At a terminal, do:```
sudo apt-get install flashplugin-nonfree
```
And you should be able to play swf files in firefox.

---

### Post by zorkerz on 2008-09-23
I already have flashplugin-nonfree and I still cannot play a .swf file from cnn.com. 

Is there anything else I can try for playing .swf?

Also I will eventually be trying to play this in windows think that will be a problem?

---

### Post by terry_gardener on 2008-09-23
in firefox, type about:plugins in the address bar and there should be shockwave flash section near the top of the page. check to see if the swf feature is enabled

---

### Post by zorkerz on 2008-09-23
yes the shockwave flash plugin is enabled

here is the video im trying to watch maybe somebody else can see if they can watch it

[http://www.cnn.com/video/#/video/health/2008/08/01/gupta.awake.brain.surgery.cnn?iref=videosearch](http://www.cnn.com/video/#/video/health/2008/08/01/gupta.awake.brain.surgery.cnn?iref=videosearch)

---

### Post by terry_gardener on 2008-09-23
yes it worked ok for me. 

i am using flash 10 rc1. 

if you want to try flash 10 rc check out 

[http://tombuntu.com/index.php/2008/08/28/test-drive-adobe-flash-player-10-rc-in-ubuntu/](http://tombuntu.com/index.php/2008/08/28/test-drive-adobe-flash-player-10-rc-in-ubuntu/)

---

