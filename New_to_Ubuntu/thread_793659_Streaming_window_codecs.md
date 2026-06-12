---
title: "Streaming window codecs"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by roc320 on 2008-05-14
Hello everyone I was wondering if you could watch WMV (asx) streams with Ubuntu 8.04. I have Mozilla Firefox 3 with some codecs installed, but is there a specific codec that I need. 

On a side note I installed the codecs to have Mplayer stream videos withing firefox, but it has been bombing out on me. Any help would be great.

---

### Post by PinkFloyd102489 on 2008-05-14
So you have the mozilla-mplayer plugin installed? It should automatically start the WMV streams.

As for ASX files, I dont know. To my knowledge, Windows Media Player is the only program that can handle them. Try opening the ASX file in a text editor to get the direct link to the video you're wanting to watch.

---

### Post by Bubba64 on 2008-05-14
Ubuntu restricted extras in add remove and the gstreamer stuff if added will cover everything you need also installing vlc helps.I think the extras cover the wmv.

---

### Post by Michael.Godawski on 2008-05-14
Open the VLC player.
File/Open Network Stream/HTTP
insert the link address to the vid and
hit OK.

---

### Post by Bradtek on 2008-05-14
Complete Streaming, Multimedia & Video How-to 
[http://ubuntuforums.org/showthread.php?t=661833&highlight=streaming](http://ubuntuforums.org/showthread.php?t=661833&highlight=streaming)


Following this should get it working.
I can usually watch a wmv stream but can not seek/skip.

---

### Post by roc320 on 2008-05-14
Thanks everyone I will try to see if I can get things to work. Thanks

---

### Post by roc320 on 2008-05-14
Ok everyone I applied the tips from the multimedia post, and things seem to be working better. I'm trying to view streaming real player format videos, with fire fox 3 with mplayer (and plugins). The video starts to cue up but the feed then stops all sudden, is there way to get the output from fire fix in the console and see what the error is to the reason why I can't view anything. Thanks

---

### Post by roc320 on 2008-05-14
Ok I did a little fooling around with Fire Fox and realized there was an area that shows what errors are happening. This is the message I get when trying to view and online real video feed: Warning: Unknown property 'displayFormat'.  Declaration dropped

Any help would be great guys thanks.

---

