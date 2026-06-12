---
title: "VLC record webcam and stream to Chrome"
date: 2011-06-09
forum: Programming Talk
---

### Post by ioan1k on 2011-06-09
Hello All,

I am currently trying to accomplish the following.

[LIST]
[*]Record a webcam stream using VLC. (done)
[*]Play that stream as it records in chrome using HTML5 Video.
[*]Control (start, stop) the recording using python, by execute commands.
[/LIST]

So far I have been able to setup the actual recording of the webcam video, but am unable to determine how to get that video to stream into chrome, or how I will be able to stop the recording.

I am using the following for recording.

```

vlc v4l2:// :v4l2-dev=/dev/video0 :v4l2-width=1280 :v4l2-height=1080 --sout "#transcode{vcodec=mpeg4,acodec=mpga,vb=800,ab=128}:standard{access=file,dst=/home/nwhiting/Desktop/capture_4.avi}"

```

---

### Post by samsunix on 2012-01-21
> **ioan1k said:**
> Hello All,

I am currently trying to accomplish the following.

[LIST]
[*]Record a webcam stream using VLC. (done)
[*]Play that stream as it records in chrome using HTML5 Video.


[http://ubuntuforums.org/showthread.php?t=1859089](http://ubuntuforums.org/showthread.php?t=1859089)

---

