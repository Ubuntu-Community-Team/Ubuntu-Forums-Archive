---
title: "Firefox, HTML5 and Youtube videos locked to 360p."
date: 2015-09-18
forum: New to Ubuntu
---

### Post by grokku on 2015-09-18
Salutations, folks.

First of all, I'd like to say that I really want to quit using windows. I tried some Linux distributions and Ubuntu was the easiest one to make my old 9800gt work without problems.
Second, I do dabble in configurations, but I'm new to this game, so go easy on me. I don't know many things.
Ok, with that out of the way.

I'm having problems with HTML5 videos on Youtube on Firefox.
Without dabbling with the about:config options, most videos work, but with only one quality setting, 360p. I did some research, and changing both media.mediasource.enabled and media.mediasource.webm.enabled to true will unlock more quality settings, but then some videos won't work at all.
I also read about messing with media.fragmented.*, but nothing seems to work.
I also read [http://ubuntuforums.org/showthread.php?t=2265679](http://ubuntuforums.org/showthread.php?t=2265679) and tried it's solutions, but they didn't work.
I do have the nVidia proprietary driver installed.

Youtube is one of the sites I use the most, and Flash is really  something I wish I could stop using, as it seems to be the way to the  future, so I'd rather avoid installing Chrome or Flash.

Currently using Firefox 40.0.3 and Ubuntu is updated.
With both settings to true: [https://www.youtube.com/watch?v=-QekUwBmckQ](https://www.youtube.com/watch?v=-QekUwBmckQ) works with all quality options and [https://www.youtube.com/watch?v=LicG16IOvss](https://www.youtube.com/watch?v=LicG16IOvss) doesn't work at all, but has all the quality settings showing. Both work with 360p only if the settings are on false.

Thanks in advance.

P.S.: sorry about any English mistakes, it is not my first language.

---

### Post by tristan16 on 2015-09-18
Ok, we can get this working in a few simple steps:

First, go to about:config in Firefox. Search for "media.mediasource" and double-click the ".enabled" and ".webm.enabled" options so that all 4 entries say true.

Now go to [www.youtube.com/html5](www.youtube.com/html5). All but 1 of the boxes should have a blue checkmark. To get that last box, we need to go to the software center.

In the Ubuntu Software Center, search for and install "gstreamer1.0-libav". Once that's done, go back to about:config in Firefox and search for "media.fragmented".

Double click "media.fragmented-mp4.exposed" and "media.fragmented-mp4.gmp.enabled" to set them to true.

Now go back to [www.youtube.com/html5](www.youtube.com/html5) and refresh the page. All of the boxes should have a blue checkmark, and you can now watch any video in any quality on YouTube. Hope this helps! :)

---

### Post by grokku on 2015-09-18
Thanks for the reply.

I installed the gstreamer1.0-libav and set all those 6 entries on about:config to true. The options were already present before I installed the library, by the way.
Checking the [www.youtube.com/html5](www.youtube.com/html5) link you provided shows all boxes checked blue, which probably means something worse is keeping some videos from playing.
As before, the quality settings on the first video show and it plays like a charm, but the second won't start, reporting that "an error occurred", without much else.
I cleared the cache after the installation and even restarted the computer, just to make sure nothing would be keeping Firefox from updating. Still nothing.

Any other possible solutions?

Thanks in advance.

---

### Post by grokku on 2015-09-18
After posting the last thing, I was messing around about:config and realised that "media.fragmented-mp4.ffmpeg.enabled" was set to false. I set it to true and both videos are playing without any problems.
I'm pretty sure I had changed that around before installing the library to no effect, so the installation probably changed something to make it possible.

Thanks for the attention and may others find light in this post.

---

### Post by tristan16 on 2015-09-21
> **grokku said:**
> After posting the last thing, I was messing around about:config and realised that "media.fragmented-mp4.ffmpeg.enabled" was set to false. I set it to true and both videos are playing without any problems.
I'm pretty sure I had changed that around before installing the library to no effect, so the installation probably changed something to make it possible.

Thanks for the attention and may others find light in this post.

Glad you got it working!

---

### Post by SmithParker on 2015-09-21
I had the same problem few days ago.
Thanks for the answer

---

### Post by Andrew_Carmer on 2015-09-24
I had the same issue after a fresh install. Thank you for the help!

---

