---
title: "Problem with mic ?"
date: 2012-10-10
forum: New to Ubuntu
---

### Post by cyb3r_sn4k3 on 2012-10-10
I am using KDE 4.9.2 on Kubuntu 12.04. I have a problem with the mic where I can hear my voice on the speakers but cant seem to record anything (tried ffmpeg and audacity)

The Code which I used for recording in ffmpeg 
```
ffmpeg -f alsa -i pulse -f x11grab -r 30 -s 1366x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -threads 0 output.mkv
```

---

