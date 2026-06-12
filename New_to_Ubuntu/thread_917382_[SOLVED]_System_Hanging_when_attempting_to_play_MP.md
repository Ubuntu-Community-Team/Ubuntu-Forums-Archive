---
title: "[SOLVED] System Hanging when attempting to play MP3"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by rideburton56 on 2008-09-11
I just downloaded my first .torrent file, and it went like a breeze.  One concern I have is that after I downloaded the files, I went and tried to play a file, just by double clicking it.  The system locked up, and I had to do a manual reboot, after which it actually froze again right after I signed in.  One more cold reboot and the system started up, and I was able to play all files out of rhythmbox.  Any advice?  The only thing I did differently the first time around was just double click, and it seemed like it opened up a different program (i believe it was totem).  Much thanks!

---

### Post by Vivaldi Gloria on 2008-09-11
> **rideburton56 said:**
> The only thing I did differently the first time around was just double click, and it seemed like it opened up a different program (i believe it was totem).  Much thanks!

1) Right click an mp3 file and choose properties. Choose another app to open with. Now ubuntu will use that app when you double click. So no more totem for mp3 files.

2) Do you have mp3 codecs installed? Start

system menu > admin > synaptic

Enable restricted and multiverse repositories from the repository settings to get a more complete list. Then click refresh. 

Now you can search and install whatever you want in synaptic. For example search and install

```
ubuntu-restricted-extras
```

which contains java, codecs, and other goodies.

---

### Post by rideburton56 on 2008-09-11
Thanks, I actually figured I would do that right away, I just wasnt sure if there was some last step to finalizing the torrent.  Much Appreciated though!

---

