---
title: "Video-maker"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by dep0 on 2012-01-30
Hi, i am trying to upload my first video on youtube and i would like some recommendation about which program to use.
Any help is welcome.

---

### Post by halitech on 2012-01-30
giving a recommendation depends on just exactly what you are trying or needing to do to the video. Do you already have a video of some sort and you want to edit it before uploading or are you trying to capture a video on your computer? We need some details to help you out.

---

### Post by dep0 on 2012-01-30
> **halitech said:**
> giving a recommendation depends on just exactly what you are trying or needing to do to the video. Do you already have a video of some sort and you want to edit it before uploading or are you trying to capture a video on your computer? We need some details to help you out.

Yes you are right.Sorry i did not mention it before.
I have some mp3 tracks and i am trying to upload them on youtube.
It's actually a video with sound only and maybe an image in the background that i want to make.

---

### Post by Double.J on 2012-01-30
Hi there!

Firstly youtube will accept a wide range of formats :) I personally choose .avi, but their list is [here]("http://support.google.com/youtube/bin/answer.py?hl=en&answer=55744")

As for which software you should use... well this is personal preference - I happen to like openshot and open movie Editor, they both follow a similar layout style to Adobe Premier Pro (Ver 2 is what I cut my teeth on) - I'd say Open Movie Editor is closer. I've also heard some good things about Lives, but haven't used it :)

It's been a couple of years(try 4) since I put any music on youtube, it does seem more common now, but I'd recommend making sure that you're not getting into a copy-write nightmare; my first couple of youtube clips (around 2006-7) were removed for breech of CW ;)

All the best!

---

### Post by halitech on 2012-01-30
> **dep0 said:**
> 
I have some mp3 tracks and i am trying to upload them on youtube.
It's actually a video with sound only and maybe an image in the background that i want to make.

so basically a slideshow is what you are going after. Not sure about Lives either but have heard of it. Another very easy to use one is Imagination but it outputs only to ogv format so unless you want to convert it to avi, it may not work.

---

### Post by halitech on 2012-01-30
> **gnu/mirow said:**
> Hi there!

It's been a couple of years(try 4) since I put any music on youtube, it does seem more common now, but I'd recommend making sure that you're not getting into a copy-write nightmare; my first couple of youtube clips (around 2006-7) were removed for breech of CW ;)

All the best!

I put a slideshow up last year to tribute a friends life after he died using Blackhawks Ships of Heaven and it's still there but I did get a notice saying it would be blocked in certain countries for possible CW violations but friends in the US and Canada were both able to view it. Seems it is getting more common now and I think as long as you don't claim the music as your own, they are being a little more lenient unless they get a complaint.

---

### Post by lisati on 2012-01-30
One thing to be aware of is that Youtube seems to do some intensive checking of soundtracks. About a year ago I uploaded a clip of an outdoor event. Youtube's system correctly identified the music that was playing in the background and warned me that I might have uploaded copyrighted material.

---

### Post by dep0 on 2012-01-31
I'll start by using Lives and/or openshot and let you know for any troubles i might have.
Thank you all for helping.

---

### Post by sudodus on 2012-01-31
> **dep0 said:**
> I'll start by using Lives and/or openshot and let you know for any troubles i might have.
Thank you all for helping.
I'm also using ***OpenShot***, to edit my amateur videos. If you want to convert videos, you can use OpenShot, but ***ffmpeg*** suits better if you want to do a batch job converting a lot of videos (for example to get a more efficient compression to save disk space, or to change the frame size or rate).

---

### Post by FakeOutdoorsman on 2012-01-31
If you like command-line you can use ffmpeg to do this. It fast because it will simply copy the audio instead of re-encoding it. The syntax will depend on the version of your ffmpeg:

Current syntax:
```
ffmpeg -loop 1 -i input.jpg -i input.mp3 -c:a copy -qscale:v 2 -shortest output.mkv
```

Old syntax:
```
ffmpeg -loop_input -i input.jpg -i input.mp3 -acodec copy -qscale 2 -shortest output.mkv
```

---

