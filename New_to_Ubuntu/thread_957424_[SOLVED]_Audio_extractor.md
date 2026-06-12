---
title: "[SOLVED] Audio extractor?"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by JacKeown on 2008-10-24
Does anyone know any programs you can use to get only the audio out of a video? Thanks

---

### Post by niyonk on 2008-10-24
I only know of Avidemux, it is a video editor | encoder
Give that a try,
Probably better options out there, but if u also want more video editing then stay with it :)

---

### Post by SuperSonic4 on 2008-10-24
you can use ffmpeg from the command line

Open up a text editor and paste the following code:

```
!/bin/bash
cd ~/[COLOR="Red"]Videos[/COLOR]
for i in *.[COLOR="Red"]flv[/COLOR]; do ffmpeg -i "$i" -acodec copy "`echo "$i" | sed -r -e 's/(.*)\.[COLOR="Red"]flv[/COLOR]$/\1.[COLOR="Red"]mp3[/COLOR]/'`"; done
```

[COLOR="Red"]Red[/COLOR] means you can change it, ~/Videos is the path to the video folder.
.flv is the format of the video and .mp3 the audio which can be changed to whatever audio file you like.

Once done save it as something (I will say ripper) and from the terminal cd to the place you saved it (it can be anywhere, mine is in /home/sonic) ```
chmod +x ripper
```

and finally from the directory you save it in: [code]./ripper[/color]

---

### Post by pyromanic123boom on 2008-10-24
VirtualDub mod does this...don't know if it works on ubuntu.

So for sure, avidemux can save the audio. Just load the video, then go to Audio --> Save Track. Then you can edit in Audacity or whatever.

---

### Post by logos34 on 2008-10-24
Transcode works great for me:

[http://ubuntuforums.org/archive/index.php/t-330856.html](http://ubuntuforums.org/archive/index.php/t-330856.html)

---

### Post by FakeOutdoorsman on 2008-10-24
I prefer ffmpeg.  It can just copy the audio stream from one container to another without the need to re-encode.  First find out the audio type:
```
ffmpeg -i inputvideofile.flv
```
You will get an output that includes the audio information:
```
Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 56 kb/s
```
Now that I know it is mp3 I can just copy the audio:
```
ffmpeg -i inputvideofile.flv -acodec copy -vn output.mp3
```

---

### Post by JacKeown on 2008-10-24
I got everything working with avidemux thanks

---

