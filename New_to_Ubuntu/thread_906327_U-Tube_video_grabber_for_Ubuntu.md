---
title: "U-Tube video grabber for Ubuntu"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by pkj on 2008-08-31
Hi,
Looking for Video Grabber for downloading videos from You-Tube

Any suggestions

pkj

---

### Post by wankel on 2008-08-31
did you give the firefox extensions a try?

[https://addons.mozilla.org/en-US/firefox/search?q=flash+download&cat=1%2C38](https://addons.mozilla.org/en-US/firefox/search?q=flash+download&cat=1%2C38)

good luck!

---

### Post by Rhubarb on 2008-08-31
There are plenty of ways to do this:


In a terminal, install the youtube-dl application:
```
sudo aptitude install youtube-dl
```
Then download a video to your home folder:
```
youtube-dl http://www.youtube.com/watch?v=ZxfSwzhSn1c
```


Or grab this program:
[http://www.getdeb.net/app/QTTube](http://www.getdeb.net/app/QTTube)
Which'll give you a nice program in your menu you can use.


Or load up the youtube page you wish to download in firefox, wait until the video is fully buffered in, then:
Places --> Home Folder
Navigate to: "/tmp"
The video should be in there, copy it somewhere in your home folder.
Then you may close firefox / navigate to a different page.


Or as wankel said, there's probably a few firefox extensions you could use aswell.

---

### Post by Sealbhach on 2008-08-31
I use the Firefox add-on video downloadhelper.

[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)

Works grand for me.


.

---

### Post by nothingspecial on 2008-08-31
You don`t need a program for this. Simply watch the video. When the bar thing at the bottom of the video has fully loaded, navigate to your tmp folder and the video will be there. Copy and paste it where you like.
:guitar:

---

### Post by pkj on 2008-08-31
Tried youtube-dl [http://in.youtube.com/watch?v=Uavzz1iqwt8&feature=related](http://in.youtube.com/watch?v=Uavzz1iqwt8&feature=related)

Getting following error
pradeep@pradeep-desktop:~$ youtube-dl [http://in.youtube.com/watch?v=fJOkkUOU7UQ&feature=related](http://in.youtube.com/watch?v=fJOkkUOU7UQ&feature=related)
[1] 7798
pradeep@pradeep-desktop:~$ Error: URL does not seem to be a youtube video URL. If it is, report a bug.

[1]+  Exit 1                  youtube-dl [http://in.youtube.com/watch?v=fJOkkUOU7UQ](http://in.youtube.com/watch?v=fJOkkUOU7UQ)
pradeep@pradeep-desktop:~$ youtube-dl [http://in.youtube.com/watch?v=Uavzz1iqwt8&feature=related](http://in.youtube.com/watch?v=Uavzz1iqwt8&feature=related)
[1] 7832
pradeep@pradeep-desktop:~$ Error: URL does not seem to be a youtube video URL. If it is, report a bug.

pkj

---

### Post by pkj on 2008-08-31
How do i identify the video in the tmp folder

pkj

---

### Post by wd5gnr on 2008-08-31
This lets you get very high quality MP4s from You Tube:

[http://googlesystem.blogspot.com/2008/04/download-youtube-videos-as-mp4-files.html](http://googlesystem.blogspot.com/2008/04/download-youtube-videos-as-mp4-files.html)

---

### Post by nothingspecial on 2008-08-31
It will look like a video file (like a bit of film tape).
I just did one to check and the video I tried was called FlashYP9jkw.
Remember once you navigate away from that web page it will be gone.
Copy it somewhere before you do.

---

### Post by Rhubarb on 2008-08-31
You should clean up the youtube URL a bit before running it with the youtube-dl program, like this:
```
youtube-dl http://www.youtube.com/watch?v=fJOkkUOU7UQ
```
(get rid of the in. before youtube, and the feature related text).

You can identify the video in the tmp folder easily, just sort by file size, it's usually the biggest one there.

---

### Post by pkj on 2008-08-31
Thanks
I was able to shift the downloaded file from the tmp folder

pkj

---

### Post by deathvalleyjoker on 2008-08-31
> **pkj said:**
> Thanks
I was able to shift the downloaded file from the tmp folder

pkj

This definitively is the easiest method by far. now can anyone recamend a file converter for Linux? The file type says Flash video, and i would liek it in a formate that could play on my zune. Thanxs

---

### Post by nothingspecial on 2008-08-31
If you`re feeling brave ffmpeg is a fabulous command line converter.
However it takes alot of reading to be able to use it properly.
If you want an easy gui then I recommend winff.
[http://www.winff.org/](http://www.winff.org/)

---

### Post by pyromanic123boom on 2008-08-31
AVIDemux! Loads different formats and converts to loads of different ones as well. I use it for my psp, and have used to for an ipod. Zune is WMV, is that right? or is it MP4 too? I don't have a zune so I forget how to encode for it...although I did it for a friend once.

---

### Post by rian tuanakotta on 2011-06-20
> **deathvalleyjoker said:**
> This definitively is the easiest method by far. now can anyone recamend a file converter for Linux? The file type says Flash video, and i would liek it in a formate that could play on my zune. Thanxs

i recommend you using this [Mobile Media Converter]("http://www.miksoft.net/mobileMediaConverter.htm")

---

