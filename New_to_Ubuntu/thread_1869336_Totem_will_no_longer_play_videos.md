---
title: "Totem will no longer play videos"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by mdavis1231 on 2011-10-25
I installed KMyMoney the other day.  I enabled kubuntu backports just to upgrade to the latest edition.  It installed a whole bunch of other packages, which I removed.  Somehow, I must have removed some things that Totem Movie Player requires to play different file types, because now, Totem Movie Player won't play any videos at all, only sound.

I've installed Gnome-Mplayer, which has no problem playing any video file type, or DVD's.

I like Totem, but does anyone know how I can fix this?  Everytime I try to play a movie, it says that I'm missing the XVID-mpeg4 codec, or the Windows Media Video 9 decoder, etc.  Or should I just stick with Gnome Mplayer from now on? :confused:

---

### Post by blade4 on 2011-10-25
Try using the terminal to open any video file in totem . This should tell you exactly what is wrong and which plugins are missing . Then just search those plugins in synaptic/google . 

If that doesn't work , try reinstalling totem from synaptic ..

---

### Post by blade4 on 2011-10-25
.

---

### Post by mdavis1231 on 2011-10-25
OK, I tried reinstalling Totem through Synaptic, and no go.  Here is the output of each type of video that I tried to open in Totem through Terminal:

flv:
** Message: Missing plugin: gstreamer|0.10|totem|H.264 decoder|decoder-video/x-h264 (H.264 decoder)
** Message: No installation candidate for missing plugins found.

avi:
** Message: Missing plugin: gstreamer|0.10|totem|MPEG-4 Video decoder|decoder-video/mpeg, mpegversion=(int)4, parsed=(boolean)true, systemstream=(boolean)false (MPEG-4 Video decoder)

mp4:
** Message: Missing plugin: gstreamer|0.10|totem|H.264 decoder|decoder-video/x-h264 (H.264 decoder)

wmv:
** Message: Missing plugin: gstreamer|0.10|totem|Windows Media Video 8 decoder|decoder-video/x-wmv, wmvversion=(int)2, format=(fourcc)WMV2 (Windows Media Video 8 decoder)

I know this sounds stupid, but are these all plugins that I can find in Synaptic to reinstall?  What do I do?  Thanks!!!

---

### Post by blade4 on 2011-10-26
Go into synaptic , search "gstreamer0.10" (without quotes) and choose reinstall/install option for the following : 

gstreamer0.10-ffmpeg
gstreamer0.10-tools
gstreamer0.10-nice
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-good
gstreamer0.10-x
gstreamer0.10-bad
gstreamer0.10-gnonlin

These are the plugins on my ubuntu lucid - there may be additional plugins on your system . But these should restore your video 

Hope this helps

---

### Post by mdavis1231 on 2011-10-26
> **blade4 said:**
> Go into synaptic , search "gstreamer0.10" (without quotes) and choose reinstall/install option for the following : 

gstreamer0.10-ffmpeg
gstreamer0.10-tools
gstreamer0.10-nice
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-good
gstreamer0.10-x
gstreamer0.10-bad
gstreamer0.10-gnonlin

These are the plugins on my ubuntu lucid - there may be additional plugins on your system . But these should restore your video 

Hope this helps

Thanks!!!

---

