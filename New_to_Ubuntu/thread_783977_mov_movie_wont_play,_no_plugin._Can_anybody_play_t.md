---
title: "mov movie wont play, no plugin. Can anybody play this?"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by philinux on 2008-05-06
[http://www.dcresource.com/reviews/panasonic/dmc_tz5-review/P1000102.MOV](http://www.dcresource.com/reviews/panasonic/dmc_tz5-review/P1000102.MOV)

Thanks.

---

### Post by avidfan on 2008-05-06
i get lots of pretty coloured pixels!

---

### Post by philinux on 2008-05-06
Ok I downloaded it to my desktop instead of trying to play it embedded. Totem crashes, and thats with the xine backend, vlc and mplayer can play it but it's not very smooth playback.

---

### Post by glennric on 2008-05-06
Plays fine for me.  I use mozilla-mplayer.  It does crash for me when I try to play it with totem-xine.

---

### Post by billgoldberg on 2008-05-06
It doesn't stream for me.

The plugin just doesn't load the video.

I can play the video in "vlc" without any problem.

---

### Post by philinux on 2008-05-06
Ok uninstalled totem-mozilla and installed mozilla-mplayer.

Embedded now plays but sound is off and very stuttery playback.

Turned compiz off made no diff.

---

### Post by glennric on 2008-05-06
Hmm, I get smooth playback with mplayer.  When I play it in the browser with mozilla-mplayer it buffers the entire 30 MB file and plays it fine.

---

### Post by philinux on 2008-05-06
It's the sound that's making the video playback stutter.

---

### Post by devilsoulblack on 2008-05-10
> **philinux said:**
> Ok uninstalled totem-mozilla and installed mozilla-mplayer.

Embedded now plays but sound is off and very stuttery playback.

Turned compiz off made no diff.
i am capable play mov on firefox but any player ? on ubuntu possible playback mov video ?

---

### Post by FuturePilot on 2008-05-10
Works here with the Mplayer plugin.

---

### Post by smokyink on 2009-05-23
Could anybody point me to the appropriate plug-ins for Mplayer to open .mov files?
I get "Could not read from resource." error message 
tnx in advance

---

### Post by philinux on 2009-05-23
I just checked this as i was searching my threads and saw this one resurrected. 

Solution is to turn flashblock addon off. The movie then streams fine. This is a default install so it's using this standard plugin. 
QuickTime Plug-in 7.2.0

    File name: /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so

Or right click and choose save target as. Plays fine once downloaded to desktop.

---

### Post by andrew.46 on 2009-05-23
Hi smokyink,

Beaten to the punch :-). I just made some coffee while the file was downloading and somebody had already answered by the time I came back! Anyway I had a look at the file which is not quite a standard mov file although this container type can hold a lot of different formats:

```

Duration: 00:00:10.00, start: 0.000000, bitrate: 25678 kb/s
Stream #0.0(eng): **[COLOR="Purple"]Video: mjpeg[/COLOR]**, yuvj420p, 1280x720, 30 tbr, 30 tbn, 30 tbc
Stream #0.1(eng): **[COLOR="Purple"]Audio: pcm_u8[/COLOR]**, 8000 Hz, mono, s16, 64 kb/s

```

A total of 10 seconds of very high bitrate video with very poor quality sound. To play offline with MPlayer no *external* codecs are required:

```

andrew@skamandros~/Desktop$ mplayer P1000102.MOV 
MPlayer SVN-r29318-4.2.4 (C) 2000-2009 MPlayer Team

Playing P1000102.MOV.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [jpeg]  1280x720  24bpp  30.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat -1
**[COLOR="Purple"]Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG)[/COLOR]**
==========================================================================
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 8000 Hz, 1 ch, u8, 0.0 kbit/0.00% (ratio: 0->8000)
**[COLOR="Purple"]Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)[/COLOR]**
==========================================================================
AO: [oss] 8000Hz 1ch u8 (1 bytes per sample)
Starting playback...
VDec: vo config request - 1280 x 720 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 3)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
A:   9.5 V:  10.0 A-V: -0.467 ct: -0.295   0/  0 23%  5%  0.5% 0 0 

Exiting... (End of file)

```

Can you play this from the terminal and see if your copy of MPlayer shows a similar output? If you are trying to play it in a browser streaming can I tell you it is 10 seconds of a train/tram going through a city and I would not bother :-). 

All the best,

Andrew

---

