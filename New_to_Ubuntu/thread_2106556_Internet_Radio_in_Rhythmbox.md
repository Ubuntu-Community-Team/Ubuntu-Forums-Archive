---
title: "Internet Radio in Rhythmbox"
date: 2013-01-19
forum: New to Ubuntu
---

### Post by jdwaugh on 2013-01-19
I want to listen to the radio stream at:
[http://www.uwplatt.edu/org/wsup/stream/wsup_high.mov](http://www.uwplatt.edu/org/wsup/stream/wsup_high.mov)

I go into rhythmbox, add the URL as a new radio station and when I click on it says it is not playing.  I checked and I have loaded all the gstreamer codecs that are in the software center.  What am I doing wrong?

---

### Post by tgalati4 on 2013-01-19
There's something wrong with the stream:

tgalati4@Dell600m-mint14 ~/Desktop $ mplayer [http://www.uwplatt.edu/org/wsup/stream/wsup_high.mov](http://www.uwplatt.edu/org/wsup/stream/wsup_high.mov)
Creating config file: /home/tgalati4/.mplayer/config
MPlayer2 UNKNOWN (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [http://www.uwplatt.edu/org/wsup/stream/wsup_high.mov](http://www.uwplatt.edu/org/wsup/stream/wsup_high.mov).
Resolving [www.uwplatt.edu](www.uwplatt.edu) for AF_INET6...

Couldn't resolve name for AF_INET6: [www.uwplatt.edu](www.uwplatt.edu)
Resolving [www.uwplatt.edu](www.uwplatt.edu) for AF_INET...
Connecting to server [www.uwplatt.edu](www.uwplatt.edu)[137.104.129.63]: 80...

Cache size set to 320 KBytes
Cache fill:  0.25% (830 bytes)   

Detected file format: QuickTime/MPEG-4/Motion JPEG 2000 format (libavformat)
[mov,mp4,m4a,3gp,3g2,mj2 @ 0xb5eff460]decoding for stream 0 failed
LAVF_header: av_find_stream_info() failed
Opening as detected format "libavformat" failed.
ISO: File Type Major Brand: Original QuickTime
Detected file format: Quicktime/MOV
No stream found.

See if you can play it using the Quicktime player in Windows.

---

