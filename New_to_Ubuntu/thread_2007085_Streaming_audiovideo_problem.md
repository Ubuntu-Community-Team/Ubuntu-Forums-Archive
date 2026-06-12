---
title: "Streaming audio/video problem"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by dotprintln on 2012-06-20
Whenever i try to play audio/video from external sources, the caching stops at 19% and then nothing happens(audio/video never starts to play).

I have given a screenshot for that problem

[http://postimage.org/image/sog9c6qs7/](http://postimage.org/image/sog9c6qs7/)

---

### Post by dotprintln on 2012-06-20
The same problem occurs for GNOME MPlayer, nothing happens after 19%.

---

### Post by andrew.46 on 2012-06-20
Does it play from the commandline:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -playlist http://www.brutalexistenceradio.com:8080/listen.pls[/COLOR]**
Resolving www.brutalexistenceradio.com for AF_INET6...
Connecting to server www.brutalexistenceradio.com[2001:470:8a81:4::1]: 8080...

Failed to connect to server with AF_INET6
Resolving www.brutalexistenceradio.com for AF_INET...
Connecting to server www.brutalexistenceradio.com[97.107.142.142]: 8080...

Cache size set to 320 KBytes
MPlayer SVN-r35003-4.7.0 (C) 2000-2012 MPlayer Team

Playing http://www.brutalexistenceradio.com:8080/.
Resolving www.brutalexistenceradio.com for AF_INET6...
Connecting to server www.brutalexistenceradio.com[2001:470:8a81:4::1]: 8080...

Failed to connect to server with AF_INET6
Resolving www.brutalexistenceradio.com for AF_INET...
Connecting to server www.brutalexistenceradio.com[97.107.142.142]: 8080...

Name   : Brutal Existence Radio
Genre  : metal
Website: http://www.brutalexistenceradio.com
Public : yes
Bitrate: 128kbit/s
Cache size set to 320 KBytes
Cache fill:  7.50% (24576 bytes)   
ICY Info: StreamTitle='Hour Of Penance - The Woeful Eucharisty';StreamUrl='http://www.brutalexistenceradio.com';
Cache fill: 15.00% (49152 bytes)   

Audio only file format detected.
==========================================================================
Opening audio decoder: [mpg123] MPEG 1.0/2.0/2.5 layers I, II, III
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mpg123] afm: mpg123 (MPEG 1.0/2.0/2.5 layers I, II, III)
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   5.3 (05.2) of -0.0 (unknown)  0.2% 56% 

```

---

