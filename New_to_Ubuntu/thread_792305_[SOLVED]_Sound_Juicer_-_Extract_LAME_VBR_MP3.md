---
title: "[SOLVED] Sound Juicer - Extract LAME VBR MP3"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by bgast1 on 2008-05-12
I was able to do this before, but I forgot and now I can't seem to get it set up in Preferences. Does anyone know how and can tell me?

---

### Post by dizee on 2008-05-13
Try```

sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
```
and then there should be an mp3 profile option in the Preferences when you restart Sound Juicer.

---

### Post by zvacet on 2008-05-13
[Here]("https://help.ubuntu.com/community/CDRipping")

---

### Post by Kenno on 2009-01-03
I wish they'd remove that LAME section from the community documentation. Juicer interfaces with LAME through gstreamer, and the gstreamer LAME plugin is thoroughly broken. [Here's why]("https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/195483/comments/22"), and [here's an alternative.]("http://wiki.hydrogenaudio.org/index.php?title=Rubyripper#Installation_on_Ubuntu_8.04") Happy ripping!

---

