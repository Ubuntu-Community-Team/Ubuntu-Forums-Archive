---
title: "MoviePlayer - Plays movies but no sound. Elonex Webbook"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by webbooknovice on 2008-08-20
Dear all, 

I am using a recently purchased Elonex Webbook and for some reason when I try and play .mov files, the video displays but there is no sound. I am using the installed Movie Player. I downloaded VLC and the opposite happened, the video sound played, but no video images.The video clips were taken using my Casio Exlim digital camera. I can open and view videos from the BBC website and Youtube and there are no issues with sound.  

Any help would be much appreciated.  

Thanks in advance

Andy

---

### Post by oliviacond on 2008-08-22
```

sudo apt-get install gstreamer0.10-plugins-bad

```
and try to play the video with movie player.

if that doesn't help, go to [http://www.mediaconverter.org](http://www.mediaconverter.org) and convert the video to mp4/avi

---

### Post by webbooknovice on 2008-08-22
> **oliviacond said:**
> ```

sudo apt-get install gstreamer0.10-plugins-bad

```
and try to play the video with movie player.

if that doesn't help, go to [http://www.mediaconverter.org](http://www.mediaconverter.org) and convert the video to mp4/avi
Thanks for this. The only videos not playing with sound now are those taking on my Casio Xlim camera. Interestingly the audio codec in Movie Player is blank. Thanks once again for your help.  Andy

---

### Post by Alan Bell on 2008-08-30
Hi,
the problem is the bad support for XV in the graphics drivers. You need to run gstreamer-properties and change the output plugin to X window system NoXV. More details and screenshot on the [webbook blog]("http://webbookblog.com/?p=44")

---

### Post by webbooknovice on 2008-08-31
Thanks Alan.
Kind regards

Andy

---

