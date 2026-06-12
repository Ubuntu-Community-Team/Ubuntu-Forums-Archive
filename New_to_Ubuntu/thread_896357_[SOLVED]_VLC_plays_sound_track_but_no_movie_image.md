---
title: "[SOLVED] VLC plays sound track but no movie image"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by webbooknovice on 2008-08-21
Dear all, having trouble with video clips on my elonex Webbook. Depending on which player I use I either get sound, or vision, not both. Any ideas as to how to resolve this would be much appreciated. Thanks. Andy  ps the system is playing Youtube videos without problem.

---

### Post by skrållarn on 2008-08-21
If you got the standard VIA C7-M 1.6Ghz with 512MB RAM and you are trying to play medium to high definition video, Im sorry to say that its probably a capacity/performance problem.
your laptop simply dont have the juice for it. try to play a lower resolution video.

...or buy a better laptop.

---

### Post by billgoldberg on 2008-08-21
> **webbooknovice said:**
> Dear all, having trouble with video clips on my elonex Webbook. Depending on which player I use I either get sound, or vision, not both. Any ideas as to how to resolve this would be much appreciated. Thanks. Andy  ps the system is playing Youtube videos without problem.

Could be a codecs problems.

Look here to install all codecs:

[http://linuxowns.wordpress.com/2008/06/23/install-audio-and-video-codecs-in-ubuntu/](http://linuxowns.wordpress.com/2008/06/23/install-audio-and-video-codecs-in-ubuntu/)

---

### Post by webbooknovice on 2008-08-21
> **billgoldberg said:**
> Could be a codecs problems.

Look here to install all codecs:

[http://linuxowns.wordpress.com/2008/06/23/install-audio-and-video-codecs-in-ubuntu/](http://linuxowns.wordpress.com/2008/06/23/install-audio-and-video-codecs-in-ubuntu/)
Many thanks will give it a try. If I use VLC opened via Wine the video will play with audio. Andy

---

### Post by Tom--d on 2008-08-21
> **webbooknovice said:**
> Many thanks will give it a try. If I use VLC opened via Wine the video will play with audio. Andy

Right click the video and click Properties. Then do to the last tab.
What codecs does it say?

---

### Post by sayakb on 2008-08-21
Open VLC. Goto Settings->Preferences. **Check** the Show advanced options (bottom right)
Now navigate to Video->Output Modules and change it to X11 output module.
Save it and restart VLC.

---

### Post by webbooknovice on 2008-08-21
> **Tom--d said:**
> Right click the video and click Properties. Then do to the last tab.
What codecs does it say?
Thanks for your assistance.  Codec for video is H.264 / AVC  There is nothing shown for audio. I've loaded VLC and it plays the video with sound and vision (via WINE).  If I can sort this one I've got the Webbook to a level where I can ditch Windows!

Andy

---

### Post by webbooknovice on 2008-08-23
> **LinuxIsInnovation said:**
> Open VLC. Goto Settings->Preferences. **Check** the Show advanced options (bottom right)
Now navigate to Video->Output Modules and change it to X11 output module.
Save it and restart VLC.
Works a treat. Many thanks, much appreciated. Andy

---

### Post by Alan Bell on 2008-08-30
you can get gstreamer to work with the same trick. Run gstreamer-properties and set the output plugin to XWindows noXV

---

