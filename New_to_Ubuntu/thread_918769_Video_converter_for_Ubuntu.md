---
title: "Video converter for Ubuntu ???"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Urvish on 2008-09-13
How can I get Video converter for Ubuntu 8.04 ?????

---

### Post by northern lights on 2008-09-13
What format(s) di you want to convert into what?

The standard commandline tool that most likely suits your needs is mplayer's [mencoder]("http://www.mplayerhq.hu/DOCS/HTML/en/index.html"). It's installable from the repositories.

---

### Post by whitethorn on 2008-09-13
Depends on what you want to convert from and to. You can take a look 

ffmpeg with Winff as a GUI.  (If you want to convert h264 then you need to use medibuntu repository)

```
sudo apt-get install ffmpeg winff
```

You could try using avidemux (not sure if it's in synaptic)

```
sudo apt-get install avidemux
```

Then there's mencoder (which is also command line), it's a part of mplayer

```
sudo apt-get install mplayer
```

I also heard you can convert some stuff using VLC, which I haven't tried out yet so I don't have any idea how.

---

### Post by bumanie on 2008-09-13
Personally I like to use devede for ease of use. > sudo apt-get install devede

---

### Post by Urvish on 2008-09-13
Can it convert the video for Ipod ????

---

### Post by northern lights on 2008-09-13
The question is:

What formats are your source files encoded in and what formats does an ipod support?

---

### Post by Urvish on 2008-09-13
It supports mp4

---

### Post by pyromanic123boom on 2008-09-13
Avidemux is a great program. MP4, AVI, FLV, basically everything you might need. Has presets for iPods and PSPs for people without a lot of video encoding knowledge. Just 

sudo apt-get install avidemux

And you should be set to encode until your computer burns up. :)

---

### Post by petronell on 2008-09-13
I personally like dvd:rip for converting to xvid.

It is in the repositories.

sudo apt-get install dvdrip

enjoy...

daveR

---

### Post by gb5757870 on 2008-09-13
I"ve been testing out dvdrip and acidrip and so far have managed to get avi files out ok at the size I want (about 700mb) but compared to other rips I've seen, the quality is nowhere near as good.

Can anyone suggest "optimum settings" for any of these programs to get really good results?

---

