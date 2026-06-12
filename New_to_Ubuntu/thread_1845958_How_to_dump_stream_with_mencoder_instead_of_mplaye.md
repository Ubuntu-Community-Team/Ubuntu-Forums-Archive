---
title: "How to dump stream with mencoder instead of mplayer?"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by honeybear on 2011-09-18
Hello,

To record the internet, i.e. avi stream from asf (x?MSWMExt=.asf), I use the mplayer way with dumpstream.

```
xterm  -e mplayer -dumpstream "$MYURL" -dumpfile internetstreams20110918-104929.avi

```

I would like to use mencoder as alternative and use pkill of it after 2 hours of recording, i.e. mencoder instead of mplayer and some use of process kill of specific recording mencoder after 2 hours. 

How would perform the operation? 

Thanks a lot :)
Regards

---

### Post by Lisiano on 2011-09-18
Something in the lines of ```
ffmpeg -i "$URL" -acodec copy -vcodec copy ./internetstream`date +%Y%m%d-%H%m%S`.avi
``` might be what you want, although it's not mencoder, but mecoder does use FFMpeg as it's backed so might be a viable solution for you.

---

### Post by honeybear on 2011-09-18
> **Lisiano said:**
> Something in the lines of ```
ffmpeg -i "$URL" -acodec copy -vcodec copy ./internetstream`date +%Y%m%d-%H%m%S`.avi
``` might be what you want, although it's not mencoder, but mecoder does use FFMpeg as it's backed so might be a viable solution for you.

thank you. I tried the code but it does not work :( 
```

 URL="http://direct.francetv.fr/regions/evt/medit-nice-direct.wsx?MSWMExt=.asf" ; ffmpeg -i "$URL" -acodec copy -vcodec copy internetstream`date +%Y%m%d-%H%m%S`.avi
```

---

### Post by Lisiano on 2011-09-18
Odd. Worked on audio streams.
Mencoder
```
mencoder $URL -oac copy -ovc copy -o internetstream`date +%Y%m%d-%H%m%S`.avi
``` Note. I had to KILL (-9) mencoder for it to exit. ^C wasn't enough for it somehow. Stream is watchable even with killing.
Now to watch and enjoy some French TV. Ah the sweet language which I understand exactly nothing.

---

### Post by honeybear on 2011-09-18
> **Lisiano said:**
> Odd. Worked on audio streams.
Mencoder
```
mencoder $URL -oac copy -ovc copy -o internetstream`date +%Y%m%d-%H%m%S`.avi
``` Note. I had to KILL (-9) mencoder for it to exit. ^C wasn't enough for it somehow. Stream is watchable even with killing.
Now to watch and enjoy some French TV. Ah the sweet language which I understand exactly nothing.



```

 mencoder http://www.montereybayaquarium.org/media/strm/mba_peng.asx  -oac copy -ovc copy -o /tmp/fi.avi
MEncoder 1.0rc3-4.4.4 (C) 2000-2009 MPlayer Team
Resolving www.montereybayaquarium.org for AF_INET6...
Couldn't resolve name for AF_INET6: www.montereybayaquarium.org
Resolving www.montereybayaquarium.org for AF_INET...
Connecting to server www.montereybayaquarium.org[209.232.226.110]: 80...
STREAM_ASF, URL: http://www.montereybayaquarium.org/media/strm/mba_peng.asx
Resolving www.montereybayaquarium.org for AF_INET6...
Couldn't resolve name for AF_INET6: www.montereybayaquarium.org
Resolving www.montereybayaquarium.org for AF_INET...
Connecting to server www.montereybayaquarium.org[209.232.226.110]: 80...
size_confirm mismatch!: 22611 28271
Error while parsing chunk header
Failed, exiting.
Resolving www.montereybayaquarium.org for AF_INET6...
Couldn't resolve name for AF_INET6: www.montereybayaquarium.org
Resolving www.montereybayaquarium.org for AF_INET...
Connecting to server www.montereybayaquarium.org[209.232.226.110]: 80...
Cache size set to 320 KBytes
success: format: 6  data: 0x0 - 0x1dc

============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...

```

here it works.
 mplayer [http://plankton.mbayaq.org/Penguins3](http://plankton.mbayaq.org/Penguins3)


I think that mencoder cannot recognize much the format of asx or m3u files ... :(

the problem is that one cannot do wget to know first where are the real url streams :(





Try here: mms://stream.tvsf.fr/live
it is a RIFF

the problem is that you cannot with mencoder
(1)  close xterm
(2) nor ctrl +c
(3) you need to do killall -e mencoder** -9**

then one get: 
> ect is undefined - no prescaling applied.
VO: [xv] 384x288 => 384x288 Planar YV12 
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)
Cannot seek in raw AVI streams. (Index required, try with the -idx switch.)
Cannot seek in raw AVI streams. (Index required, try with the [COLOR="Red"]-idx sw[/COLOR]

---

### Post by Lisiano on 2011-09-18
Why do you think you can't use wget?
```
#!/bin/sh
cleanup()
(
rm /tmp/url
killall -9 mencoder
kill $PPID
)

read URL
trap cleanup 1 2 3 6
wget $URL -O /tmp/url
if grep '<ASX version =' /tmp/url; then mencoder "`grep '<Ref href=\"' /tmp/url | grep -v '<!--' | cut '-f2' '-d"'`" -oac copy -ovc copy -o internetstream`date +%Y%m%d-%H%m%S`.avi &
else mencoder $URL -oac copy -ovc copy -o internetstream`date +%Y%m%d-%H%m%S`.avi &
fi
while :; do sleep 1s; done
```
Short script on that ASX stream. We get the URL, check that it has something about a ASX version then we try to find its URL. If we fail to find information about the ASX version, pass the URL to mencoder instead.
Also for the "Cannot seek in raw AVI streams" just pass -forceidx or -idx to mplayer when playing ```
mplayer -forceidx internetstream20110919-030933.avi
```

---

### Post by honeybear on 2011-09-19
> **Lisiano said:**
> Why do you think you can't use wget?
```
#!/bin/sh
cleanup()
(
rm /tmp/url
killall -9 mencoder
kill $PPID
)

read URL
trap cleanup 1 2 3 6
wget $URL -O /tmp/url
if grep '<ASX version =' /tmp/url; then mencoder "`grep '<Ref href=\"' /tmp/url | grep -v '<!--' | cut '-f2' '-d"'`" -oac copy -ovc copy -o internetstream`date +%Y%m%d-%H%m%S`.avi &
else mencoder $URL -oac copy -ovc copy -o internetstream`date +%Y%m%d-%H%m%S`.avi &
fi
while :; do sleep 1s; done
```
Short script on that ASX stream. We get the URL, check that it has something about a ASX version then we try to find its URL. If we fail to find information about the ASX version, pass the URL to mencoder instead.
Also for the "Cannot seek in raw AVI streams" just pass -forceidx or -idx to mplayer when playing ```
mplayer -forceidx internetstream20110919-030933.avi
```

the problem is that if you get various URL links, so various formats, then wget could download the whole thing and it would take lot of time? 

I could for instance given an various possible links : 
```
http://178.159.0.80:7486/listen.pls 
http://72.13.93.186/cartoonclassics 
http://players.creacast.com/creacast/france_info/playlist.m3u 
http://direct.francetv.fr/regions/evt/medit-nice-direct.wsx?MSWMExt=.asf 
http://plankton.mbayaq.org/Penguins3 

```
I was wondering whether it could be more universal. For instance, vlc retrieve let's call it "intelligently" the urls, and play them rather without user intervention. 

Cheers

---

### Post by Lisiano on 2011-09-19
One way would be to first analyze the URL itself for possible information, for those links you posted below, searching for m3u, pls, asf and analyze them by assuming that they are containers and writing multiple if statements and elseif statements, or something like Case. I don't know how to use case though. After that in most cases we download the $URL, but as you said, it might be data, if so we can set a sensible timeout after which wget will get killed if the output is not plaintext, then it won't be so bad. After that continue as before.

Also I noticed that VLC can do what you are trying to achieve [http://wiki.videolan.org/Documentation:Streaming_HowTo/Command_Line_Examples](http://wiki.videolan.org/Documentation:Streaming_HowTo/Command_Line_Examples)

Ofc if someone took the time it would be possible to perfect the little script I wrote for ASX streams. You can also always create different scripts for different stations, for example a script with the URL already predefined.

---

### Post by honeybear on 2011-09-23
> **Lisiano said:**
> One way would be to first analyze the URL itself for possible information, for those links you posted below, searching for m3u, pls, asf and analyze them by assuming that they are containers and writing multiple if statements and elseif statements, or something like Case. I don't know how to use case though. After that in most cases we download the $URL, but as you said, it might be data, if so we can set a sensible timeout after which wget will get killed if the output is not plaintext, then it won't be so bad. After that continue as before.

Also I noticed that VLC can do what you are trying to achieve [http://wiki.videolan.org/Documentation:Streaming_HowTo/Command_Line_Examples](http://wiki.videolan.org/Documentation:Streaming_HowTo/Command_Line_Examples)

Ofc if someone took the time it would be possible to perfect the little script I wrote for ASX streams. You can also always create different scripts for different stations, for example a script with the URL already predefined.

I installed vlc-nox
isnt it only  a console? Does VLC without GUI exists?

---

