---
title: "Convert .divx"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by ozbolt on 2008-07-31
I would really need this becouse I have Wievty (phone) that makes really good image in video .divx, so if there is anything like I would apprieciate it. I put in kubuntu, but it doesn't matter witch one is.

---

### Post by neurostu on 2008-07-31
What are you trying to do? 

Convert format123 --> divx?
convert divx --> format123?

Please explain more of your problem.

---

### Post by philinux on 2008-07-31
ffmpeg can do it but it's a command line utility.

[http://www.smorgasbord.net/converting-video-in-linux-using-ffmpeg-and-mencoder/](http://www.smorgasbord.net/converting-video-in-linux-using-ffmpeg-and-mencoder/)

Scroll down the page for the convertion bit.

---

### Post by gjoellee on 2008-07-31
check this out:
[http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016)

---

### Post by ozbolt on 2008-07-31
philinux, look like I'll have to study this thing, becouse, gjoellee, this thinge doesn't have option for .divx (not .avi or somethinge) ang it also don't works (how typical for me), so if there is any other ideas bring it on or I'll do it the hard way.

---

### Post by halitech on 2008-07-31
other then your starting format is .divx we don't know what you want to do with the files. What is your ultimate destination for the files? IE. Youtube, DVD, mpg, email, etc?

---

### Post by ozbolt on 2008-07-31
Oh, I am sorry my output format is .divx. I am sorry I made my self so unclear. I meen the .divx that is created by divx converter in Windows envirement. I am sorry for miss understanding.

---

### Post by halitech on 2008-07-31
ok, so you HAVE a divx file and you want to do something with it which is ..... ??

---

### Post by ozbolt on 2008-07-31
OMG still unclear. I have thousands of movies or files, witch I want to convert (not all but some of them) into .divx. So the created file name will be Somethinge.divx (And the starting file would be Somethinge.avi or Somethinge.mpg ,...).

---

### Post by halitech on 2008-07-31
we're here to help but we aren't mind readers so we have to peice things together as you tell us and it sounded like your phone created a divx that you wanted to do something with.

---

### Post by RomeReactor on 2008-07-31
Hi. A more complete explanation of why you want to convert the files will help us help you.

Is there any particular reason you want to transcode the videos to divx (for example, to upload to a website, or to play them in another device)? Do the avi and mpg files work correctly in your system? Bear in mind that extensions such as .avi or .mpg are containers for codecs, not actual codecs themselves.

As for the divx codec itself, according to Wikipedia it uses **MPEG-4 Part 2 compression** (MPEG-4 ASP), which [AviDemux]("http://en.wikipedia.org/wiki/Avidemux") can encode to. You can find AviDemux-QT in the repositories, using Adept/Synaptic, or form Konsole:
```
sudo aptitude install avidemux-qt
```

---

### Post by neurostu on 2008-08-01
If you have a large number of files to convert... you should consider using gstreamer to transcode, this can be done in the command line... then write a shell script that will convert everything, then run it and you're done (it may take some time to transcode everything but it should be able to do it)

---

