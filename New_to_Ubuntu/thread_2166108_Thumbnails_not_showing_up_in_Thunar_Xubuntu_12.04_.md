---
title: "Thumbnails not showing up in Thunar Xubuntu 12.04 64-bit"
date: 2013-08-07
forum: New to Ubuntu
---

### Post by marinecomm on 2013-08-07
For some reason Thunar is not showing thumbnails for some of the images on my computer. It doesn't seem to be any particular type of file format. Some images have thumbnails and some don't. I've checked around the boards and I couldn't find anyone who had my particular problem. Any ideas or suggestions? Thank you.

---

### Post by hansdown on 2013-08-07
Hi marinecomm.

Can you right click the file, and click 

```
properties
```

See what the name of the file is.

---

### Post by marinecomm on 2013-08-07
They are various image and video files

---

### Post by hansdown on 2013-08-07
> **marinecomm said:**
> They are various image and video files

Thanks.

Are you at liberty to share their file names?

It will help narrow down where the problem may be.

---

### Post by marinecomm on 2013-08-07
There are WAY too many files to name. It's becoming a PITA because I'm trying to change some of the icons on my system and I'm having to resort to clicking on each .png file to see if it's the one I need. I've also been transcoding videos. Any new video that gets produced has a default icon and not a thumbnail.

---

### Post by hansdown on 2013-08-07
With the available info, I have two possible fixes.

1- Open your picture folder, and click

```
edit>preferences>display

```
If you click on 

show thumbnails

make sure never is** not** checked.

2- This will require us to know, **how** you transcoded the files.

---

### Post by marinecomm on 2013-08-07
'show thumbnails' is definitely checked and I transcoded the videos using Arista.

---

### Post by hansdown on 2013-08-07
My favorite transcoder is  Arista.

Are you getting permission problems?

---

### Post by marinecomm on 2013-08-07
not at all. it's been working just fine for me. it's just that whatever format I transcode a video into it doesn't have a thumbnail. one thing I have noticed while looking at these files is that once I look at the file it then generates a thumbnail for it but it's still proving a pain to click on each icon just to find the one that I want. shouldn't the system automatically generate a thumbnail for a video or image when it is put onto the computer without having to view it?

---

### Post by hansdown on 2013-08-07
You're right, it should generate a thumbnail for each.

Mine behaves exactly the same as your system, (that has been bugging me, too).#-o

This problem also happens in linux mint, not that that is helpful.

---

### Post by marinecomm on 2013-08-07
ok, was doing some more research using bing and came across this forum post:

[http://superuser.com/questions/258633/why-is-thunar-not-creating-and-showing-thumbnails-of-images]("http://superuser.com/questions/258633/why-is-thunar-not-creating-and-showing-thumbnails-of-images")

When I issued the command it seems to have worked except that the first icon in the folder does not automatically receive a thumbnail.

---

### Post by marinecomm on 2013-08-08
ok, was doing some more research using bing and came across this forum post:

[http://superuser.com/questions/258633/why-is-thunar-not-creating-and-showing-thumbnails-of-images]("http://superuser.com/questions/258633/why-is-thunar-not-creating-and-showing-thumbnails-of-images")

When I issued the command it seems to have worked except that the first icon in the folder doesn't not automatically receive a thumbnail.

---

### Post by marinecomm on 2013-08-08
sorry for the double post

---

### Post by hansdown on 2013-08-08
> **marinecomm said:**
> ok, was doing some more research using bing and came across this forum post:

[http://superuser.com/questions/258633/why-is-thunar-not-creating-and-showing-thumbnails-of-images]("http://superuser.com/questions/258633/why-is-thunar-not-creating-and-showing-thumbnails-of-images")

When I issued the command it seems to have worked except that the first icon in the folder does not automatically receive a thumbnail.

Nice idea.

I've been looking too.

The maintainer of tumbler says, " tumbler no longer contains gstreamer-based thumbnailer, as ffmpeg should be enough.

There must be more.

[https://bugs.archlinux.org/task/33168](https://bugs.archlinux.org/task/33168)

---

### Post by hansdown on 2013-08-09
I've tried adding

```
ffmpegthumbnailer4
```

Have to see if it helps.

---

### Post by marinecomm on 2013-08-09
The solution that worked for me was the one I stated in post #11, which I got from this thread:

[http://superuser.com/questions/258633/why-is-thunar-not-creating-and-showing-thumbnails-of-images]("http://superuser.com/questions/258633/why-is-thunar-not-creating-and-showing-thumbnails-of-images")

I'm not having any issues with thumbnails not showing up now.

---

### Post by hansdown on 2013-08-09
> **marinecomm said:**
> The solution that worked for me was the one I stated in post #11, which I got from this thread:

[http://superuser.com/questions/258633/why-is-thunar-not-creating-and-showing-thumbnails-of-images]("http://superuser.com/questions/258633/why-is-thunar-not-creating-and-showing-thumbnails-of-images")

I'm not having any issues with thumbnails not showing up now.

I somehow missed your double post.  :)

---

### Post by marinecomm on 2013-08-09
yeah, i was having some internet connectivity issues at the time lol

---

