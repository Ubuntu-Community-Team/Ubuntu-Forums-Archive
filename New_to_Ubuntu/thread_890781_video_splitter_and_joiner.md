---
title: "video splitter and joiner"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-08-15
which is the best GUI based video splitter cum joiner,that can run on my ubuntu 8.04.also,kindly suggest a video format converter.

---

### Post by wolfen69 on 2008-08-15
check [this]("http://www.getdeb.net/category.php?id=12") page for a video splitter/joiner. use ffmpeg along with winff to convert videos.

---

### Post by Rhubarb on 2008-08-15
A friend of mine uses avidemux to cut / join videos.
```
sudo aptitude install avidemux
```
You'll then find it in Applications --> Sound & Video --> Avidemux (GTK+)

I haven't used it myself, as I don't do that much video editing.
As for video format converting, handbrake [http://ubuntuforums.org/showthread.php?t=813632](http://ubuntuforums.org/showthread.php?t=813632) is supposed to be good and easy to use.

Personally I like to play with the command line, using **mencoder** / **ffmpeg** to encode, and **cat** to join mpeg video streams.

---

### Post by johnjoe on 2008-12-22
Hi

Ubuntu Studio 7.10

I have not got as far as joining yet (apart from using qdvdauthor to produce DVD's from a list mpeg2 files) but have had very good results with dvbcut in splitting and cutting mpeg files.
It needs the files as .mpg rather than .mpeg

Regards

John

---

