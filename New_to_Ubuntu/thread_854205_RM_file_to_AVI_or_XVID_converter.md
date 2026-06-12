---
title: "RM file to AVI or XVID converter"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by appoloin on 2008-07-09
hi again,

another question. whats a good program to use to convert .rm movies to avi or xvid?

---

### Post by billgoldberg on 2008-07-09
> **appoloin said:**
> hi again,

another question. whats a good program to use to convert .rm movies to avi or xvid?

I'm not familiar with a .rm file.

Is that real media?

You can convert it with mencoder, but that's cli only.

```
sudo apt-get install mencoder
```

The command for converting a .rm file to avi is this:

```
mencoder video1.rm -oac mp3lame -ovc xvid -xvidencopts bitrate=150 -srate 44100 -af resample=44100 -o video1.avi
```

This is just copy/paste from another site, I don't know if this will work.

You would need to replace video1.rm with the path to the video.

For example /home/usernamer/Videos/video.rm.

Idem dito for the video1.avi.

You could try if ffmpeg can convert the file.

Install the ffmpeg version (sudo apt-get install ffmpeg) from the [medibuntu repo]("http://linuxowns.wordpress.com/2008/06/23/install-audio-and-video-codecs-in-ubuntu/")(!!), and install the winff.deb file [here]("http://www.winff.org/index.php?option=com_content&view=category&layout=blog&id=34&Itemid=54").

Normally winff would be the easiest way to convert videos, but I don't know if it will handle real media files.

---

### Post by OmahaVike on 2011-12-16
i know i'm very late to the party, but had the same question and found a solution.  there's a blog posting here that describes using ffmpeg and mencoder to do the trick...

[http://blogs.walkerart.org/newmedia/2008/05/29/video-conversion-ffmpeg-mplayer/]("http://blogs.walkerart.org/newmedia/2008/05/29/video-conversion-ffmpeg-mplayer/")

I first did this:

```
 mencoder MyHouse.rm -ni -o MyHouse.flv -oac mp3lame -lameopts abr:br=56 -srate 22050 -ovc lavc -lavcopts vcodec=flv:vbitrate=300:mbd=2:mv0:trell:v4mv:cbp:last_pred=3 -fps 30.000 -ofps 24 -mc 1 -of lavf
```

and then used handbrake for the rest:

```
HandBrakeCLI -i MyHouse.flv -o MyHouse.mp4 --preset="Normal"
```

hope it helps someone out there.  not a lot of documentation for converting those ten-year-old videos from RM.

---

### Post by nothingspecial on 2011-12-16
[attach]209228[/attach]

---

