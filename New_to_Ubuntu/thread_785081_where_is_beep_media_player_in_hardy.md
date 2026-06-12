---
title: "where is beep media player in hardy???"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by scottslinux on 2008-05-07
I just did a clean install of hardy and when I went to install beep media player using adept, it was not there.  I enabled all of the repositories and then tried it in synaptic.  No luck.  the only version avail in hardy seems to be bmpx the experimental version which cannot be skinned. I am looking for the original.  How can I install it without having to compile and without disrupting my repository list.  Thanks for you help.


Scott

---

### Post by kesman on 2008-05-07
Seems like it isn't supported by Hardy. Maybe try some other media player? For Winamp-like, try audacious.

---

### Post by vishzilla on 2008-05-07
You can install Audacious, which is a fork of Beep. There is a BMPx in the repo, I haven't tried it out. Audacious is good.

---

### Post by scottslinux on 2008-05-07
thanks for the quick reply.  Can I skin audacious???

Scott

---

### Post by kesman on 2008-05-08
Just a little google search and this is what I found:
[http://audacious-media-player.org/index.php?title=Skins](http://audacious-media-player.org/index.php?title=Skins)

---

### Post by DirtDawg on 2008-05-08
Audacious is a better choice in most cases, but if you need or prefer beep for whatever reason, there are xmms (basically the same thing as beep) packages available. Links [here]("http://ubuntuforums.org/showthread.php?t=774461").

---

### Post by sujoy on 2008-05-08
never used bmp, audacious is good enough, although IMO it doesn't seem to integrate that well with the rest of the apps.

btw, whats so special about bmp?

---

### Post by scottslinux on 2008-05-08
Thank you everyone for all of the assistance.  I was not ware of the lineage of the whole xmms, beep, audacious development.  Audacious works very well and of course looks the same on the desktop.  I just reinstalled back to gutsy from Hardy for stability reasons and in doing so have learned alot.  

Thanks Again
Scott

---

### Post by ps2key on 2008-05-08
Beep (BMPx) has a great GUI for radio streams. I don't have much time usually so I installed BMP from the gnome package app (deb I guess). It starts up fine. When I try to play a radio stream, BMP immediately closes. It worked great on the previous ubuntu version. I don't doubt that Audacious is a better player overall but BMPx met my needs well. I'll just have to get off my duff and see how to get streams playing.

---

### Post by rykel on 2008-06-08
I am trying to install beep-media-player because I am trying to install mp3splt-gtk on Hardy, which requires beep-media-player. bmpx does NOT work as a substitute.

Any help?

---

### Post by scottslinux on 2008-06-08
I have been using audacious and it integrates pretty well. It uses winamp skins so it looks just like bmp.

Scott

---

### Post by wawadave on 2008-09-01
ok i had this same trouble and installed the debian one here
[http://packages.debian.org/etch/i386/beep-media-player/download](http://packages.debian.org/etch/i386/beep-media-player/download)
solved that part of my problem

bit late for you but may help others trying to install mp3splt

---

### Post by optimix on 2008-09-05
You can also try installing the latest version of mp3splt-gtk (0.5) which supports Audacious instead of Beep Media Player.

---

### Post by Too Late on 2008-09-05
> **wawadave said:**
> ok i had this same trouble and installed the debian one here
[http://packages.debian.org/etch/i386/beep-media-player/download](http://packages.debian.org/etch/i386/beep-media-player/download)
solved that part of my problem

bit late for you but may help others trying to install mp3splt
The Ubuntu package which still exists in Feisty repos works fine in Hardy.
[http://packages.ubuntu.com/feisty/i386/beep-media-player/download](http://packages.ubuntu.com/feisty/i386/beep-media-player/download)

That's not an absolute perfect player, but it's by far the best basic player I've used in Linux. And I've tried very many. For example, Audacious has much worse "response" in its buttons (=laggy) and there's also a volume control bug (hard to explain, but it's easy to find when you change the volume before and after you open a new file).

---

