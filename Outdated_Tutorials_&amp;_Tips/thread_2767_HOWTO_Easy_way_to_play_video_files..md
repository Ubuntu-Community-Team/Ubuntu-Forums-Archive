---
title: "HOWTO: Easy way to play video files."
date: 2004-10-31
forum: Outdated Tutorials &amp; Tips
---

### Post by tanari on 2004-10-31
There is easy way to play video files!
Enable in synaptic universe repositories and install vlc and gvlc (type videolan in search window). This is all :). Watch movies.

in terminal it should look like this:
sudo apt-get update
sudo apt-get install vlc
sudo apt-get install gvlc

---

### Post by Abumosmar on 2004-11-28
[QUOTE=tanari]There is easy way to play video files!
Enable in synaptic universe repositories and install vlc and gvlc (type videolan in search window). This is all :). Watch movies.

in terminal it should look like this:
sudo apt-get update
sudo apt-get install vlc
sudo apt-get install gvlc[/QUOTE]

I'm having problem to get vlc work properly on my external monitor. it works great on the laptop but on the external monitor it's just black. any idea how to solve this?

---

### Post by HerrFickensie on 2004-11-29
[QUOTE=Abumosmar]I'm having problem to get vlc work properly on my external monitor. it works great on the laptop but on the external monitor it's just black. any idea how to solve this?[/QUOTE]
I know that in Windows XP ( :mad: ) you had to set the external monitor as the primary monitor to view video on it. Find the linux command to do that and you're in business

---

### Post by x03 on 2004-11-30
Can I get VLC to play WMV3 files?

---

### Post by Murmex on 2004-12-03
[QUOTE=x03]Can I get VLC to play WMV3 files?[/QUOTE]
 Basically vlc can play a wide range of video format...
WMV files are sometimes a bit tricky but it's getting better with latest version, so it's probably interesting to get the last version from hoary (0.8.1)

I don't find gvlc so interesting and I really prefer the basic interface coming with wxvlc.

---

### Post by alex-gurgel on 2005-01-29
[QUOTE=Murmex]Basically vlc can play a wide range of video format...
WMV files are sometimes a bit tricky but it's getting better with latest version, so it's probably interesting to get the last version from hoary (0.8.1)

I don't find gvlc so interesting and I really prefer the basic interface coming with wxvlc.[/QUOTE]

Unfortunally VLC doesn't play WMV3 files.... I've donwloaded all plugins and using VLC 0.8.1 from Hoary and can't play this type of media.
I only have sound, no image. If I start VLC from console I have this message:
"[00000272] main decoder error: no suitable decoder module for fourcc `WMV3'.
VLC probably does not support this sound or video format."

Any suggestions ?

---

### Post by fritzel67 on 2005-01-29
I tried the "apt-get install vlc" command, but what's returned are a bunch of uninstallable dependencies (i.e. libdvdplay0, liddvdread2, libpng2, etc).

Any ideas?

Thanks!

---

### Post by fritzel67 on 2005-01-29
Okay, I figured out that I needed to add the additional repositories. I now have VLC installed, and can manage to get audio out of an MPEG-2 file, but the video screen is black. Any suggestions would be greatly appreciated! Thanks.  :confused:

---

### Post by fritzel67 on 2005-01-30
Well, it turns out I have answered my own questions! VLC is working fine, but it's my old laptop (CPiA 366 w/ only 2.5MB video RAM) that can't handle an MPEG-2 stream. It can handle MPEG-1 streams though.

---

### Post by redneckr1 on 2005-02-21
can it play mp4's

---

### Post by gylf on 2005-02-21
[QUOTE=redneckr1]can it play mp4's[/QUOTE]
Yes, VLC will play MPEG-4 aacPlus.

---

### Post by cdhotfire on 2005-02-22
wow, thxs for this one. \\:D/

---

### Post by LongTooth on 2005-02-22
Installed VLC and haven't fully tested it. But I did download a .mov (Quicktime) file. VLC plays it but no sound. How can I address this. What about adding codecs? Thanks.

---

### Post by PaTTeX on 2005-03-21
hello all

i have no sound in vlc 

```
[00000269] mpeg_audio decoder: MPGA channels:2 samplerate:44100 bitrate:160
[00000273] oss audio output error: cannot open audio device (/dev/dsp)
[00000273] main audio output error: couldn't find a filter for the conversion
[00000273] main audio output error: couldn't set an output pipeline

```

any idea ?

---

### Post by Riggs on 2005-04-09
I tried this, but it didn't work.  Everything seems to play fine in xine though :)

---

