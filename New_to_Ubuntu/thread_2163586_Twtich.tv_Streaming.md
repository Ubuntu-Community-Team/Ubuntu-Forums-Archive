---
title: "Twtich.tv Streaming?"
date: 2013-07-18
forum: New to Ubuntu
---

### Post by sci4me on 2013-07-18
Hey guys! So basically, my twtich tv streaming script randomly quit working... it started giving this error:
```

[x11grab @ 0xab2f20] Couldn't parse video size.
:0.0: Invalid argument

```

Uhm... and i didnt change anything... so....... help?!?!?! Heres the script:
```

#! /bin/bash
INRES=”1600×900&#8243; # input resolution
OUTRES=”1280×720&#8243; # Output resolution
FPS=”30&#8243; # target FPS
QUAL=”fast”
STREAM_KEY=$(cat ~/.twitch_key)


avconv \
-f x11grab -s $INRES -r “$FPS” -i :0.0 \
-f alsa -ac 2 -i pulse \
-vcodec libx264 -s $OUTRES -preset $QUAL \
-acodec libmp3lame -ar 44100 -threads 6 -qscale 3 -b 712000 -bufsize 512k \
-f flv “rtmp://live.twitch.tv/app/$STREAM_KEY”

```

Dont get how something that works can just randomly break... ffs... but yeah, i REALLY need this fixed ASAP! Please help! Thanks!

---

