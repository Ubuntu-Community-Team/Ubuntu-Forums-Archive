---
title: "Using our laptop as a camcorder/video-recorder"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by hanzj on 2012-07-23
What programs do you recommend to use our laptop's internal webcam and small mic as a makeshift video-recorder?

We will leave the laptop unmoved, on a table.

We have the Gnome DE.

---

### Post by NikTh on 2012-07-24
Hi , 
i suggest , ffmpeg.. open a terminal and give this command
```
ffmpeg -f alsa -ac 2 -i pulse  -f video4linux2 -i /dev/video0  -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 -s  320x240   -r 30  -y  video.avi
```Maybe it needs to change the /dev/video0 with yours specific. 

You can terminate the process with Ctrl+C . 
Then you will find a video.avi file in your home.. open it and see if meet your needs.

**Guide: **[http://ubuntuforums.org/showthread.php?t=1710642](http://ubuntuforums.org/showthread.php?t=1710642)

Thanks

---

### Post by deadflowr on 2012-07-24
Cheese.If you can get it to work right, I have, so you should too.

---

### Post by Bufeu on 2012-07-24
Use Cheese:
```
sudo apt-get install cheese --install-suggests
```

---

### Post by hanzj on 2012-07-24
deadflowr and bufeu, I have downloaded cheese. It doesn't seem to record audio though, just video.

---

### Post by Bufeu on 2012-07-24
> **hanzj said:**
> deadflowr and bufeu, I have downloaded cheese. It doesn't seem to record audio though, just video.
[http://ubuntuforums.org/showthread.php?t=1148126](http://ubuntuforums.org/showthread.php?t=1148126)

---

### Post by hanzj on 2012-07-24
thanks, bufeu

---

