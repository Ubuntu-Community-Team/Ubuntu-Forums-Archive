---
title: "[SOLVED] Deinterlacing in Totem"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by kyalee on 2008-11-02
I upgraded to Intrepid a few days ago, clean install and so far everything is working well. Except, I'm having trouble playing a few videos. Not all of them, but one or two videos that used to play fine are now playing with messed up video. The sound is fine, but the video is squiggly and has green lines running through it. Last time I had this problem, I just unclicked the 'deinterlace' option in Totem and all was well. This time out, I can't find the 'deitnerlace' option. Did they take it out or am I just being stupid?

Any help would be appreciated. :)

---

### Post by mc4man on 2008-11-02
> Did they take it out or am I just being stupid?

Well it's certainly not you

Not 100% sure because I don't use totem-gstreamer ever but it may have been removed as an option because it didn't work. See here
[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/257818](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/257818)

---

### Post by kyalee on 2008-11-03
Huh. Interesting. I never really used the option except the one time it accidentally got clicked and started messing up a few of my videos.

Interestingly, I have the same problem in Dragon Player. (Haven't tried vlc.) I'm pretty sure I have all the needed codecs, so I'm not sure what it is.

---

### Post by philinux on 2008-11-03
I use the totem plugin for firefox but for dvd's etc I use VLC it's much nicer.

Have you checked system>admin>hardware drivers to make sure your graphics card is getting the proper driver.

---

### Post by mc4100 on 2008-11-03
I don't know if deinterlacing is the problem, but you **can** turn it off:
[list][*]Press Alt + F2
[*]Type "gconf-editor" and press enter
[*]Expand "Apps", in the left pane
[*]Click on the "Totem" entry
[*]Un-check the "Deinterlace" box in the right pane[/list]

---

### Post by kyalee on 2008-11-03
It says no proprietary drivers are being used on my system.

Also, I ran the hardware testing app and the video test came back fine.

---

### Post by kyalee on 2008-11-03
Oh, cool, thank you.

It didn't solve the problem, but it's good to know how to get to those options.

---

### Post by kyalee on 2008-11-03
Okay. I downloaded VLC and the videos are working fine with that player. Still not sure what the problem was.

---

### Post by mc4100 on 2008-11-03
> **kyalee said:**
> Still not sure what the problem was.

Have you tried changing the default output in the video tab of the Multimedia Systems Selector?

Simple to do:
Alt + F2
"gstreamer-properties"
"Video" tab
Change default output and test.

---

