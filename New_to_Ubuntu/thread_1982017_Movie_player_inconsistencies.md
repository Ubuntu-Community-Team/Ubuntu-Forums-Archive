---
title: "Movie player inconsistencies"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-05-17
Hi all

i have a bunch of mp4 music videos. Some movie player will play, others wont. They will all play with VLC media player.  Isn't it odd that movie player cant (or wont) play some files and not others, when they are all of the same format and extension. 
Any ideas?

Glenn.

---

### Post by cholericfun on 2012-05-17
well, there arent necessarily in the same format.
even when using widely available formats like mp3 jpg avi, there are always some little glitches between "versions" that arent really supposed to happen.

programming rules arent strict mathematics, the running code is => hence the errors

---

### Post by Hadaka on 2012-05-17
Your VLC player is probably working with those files because,and im guessing
you also have loaded ubuntu restricted extras. Just today, after trying to get
my vlc player to revive after an unknown melt down, it came to life, and now
plays encrypted type dvd's. movie player refused to even think about playing
the dvd i was using to test with. Now,, both vlc and movie player have no problem
playing encrypted files. By the way, i also loaded restricted extras and that didnt 
help. after much frustration and ubuntu forum search, i found the cure. here it is.
hopefully it will allow you to play what you want with whatever player you choose.
good luck.
[http://ubuntuforums.org/showthread.php?t=1935072&highlight=libdvdcss&page=2](http://ubuntuforums.org/showthread.php?t=1935072&highlight=libdvdcss&page=2)

---

### Post by mcduck on 2012-05-18
> **Senior_Buckethead said:**
> Hi all

i have a bunch of mp4 music videos. Some movie player will play, others wont. They will all play with VLC media player.  Isn't it odd that movie player cant (or wont) play some files and not others, when they are all of the same format and extension. 
Any ideas?

Glenn.

They are all in the same *container format*, but that doesn't mean the video would actually be in the same format.

.MP4 is a video container file, not a video format. So it can include audio and video tracks encoded in many different formats.


...and also like Hadaka says above, VLC uses it's own codecs while most of the other movie players are using Gstreamer codecs instead.

---

