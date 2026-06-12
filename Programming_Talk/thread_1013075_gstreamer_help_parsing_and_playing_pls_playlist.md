---
title: "gstreamer: help parsing and playing pls playlist"
date: 2008-12-16
forum: Programming Talk
---

### Post by wolterh on 2008-12-16
I have found no tutorial on how to open and play a playlist with gstreamer, so I gently ask here in hope someone will provide some knowledge.

As an example, I want to play this pls file.
```



[playlist]

numberofentries=6



File1=http://212.72.165.18:9412

Title1=Dogglounge Radio(96)

Length1=-1





File2=http://hive.rockandrollhosting.com:9020

Title2=Dogglounge Radio(96)

Length1=-1





File3=http://209.200.168.18:8000

Title3=Dogglounge Radio(96)

Length1=-1





File4=http://http://tank.rockandrollhosting.com:9024

Title4=Dogglounge Radio(96)

Length1=-1





File5=http://66.119.176.18:8000

Title5=Dogglounge Radio(96)

Length1=-1





File6=http://66.165.191.94:8000

Title6=Dogglounge Radio(96)

Length1=-1


```

Its from [http://www.dogglounge.com](http://www.dogglounge.com), very good electronic/techno/etc for those who like it.

---

### Post by Aruna Hewapathirane-&#3461;&#3515;&#3536;&#3499; on 2010-08-12
In your example play-list:

File6=http://66.165.191.94:8000
Title6=Dogglounge Radio(96)
Length1=-1

Pass the URL ([http://66.165.191.94:8000](http://66.165.191.94:8000)) to gstreamer like this:

```
gst-launch-0.10 playbin uri="http://66.165.191.94:8000"
```

---

