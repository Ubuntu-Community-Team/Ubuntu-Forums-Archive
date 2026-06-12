---
title: "Can't Watch Videos"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by hack13 on 2008-11-05
Hi, first off I must applaud the programmers. This is do to my computers motherboard died, I had to build a computer out of 4 old outdated computers that did not work separate, but together I was able to make one that could turn on. I hooked my up my hard drives and it booted right up and everything was exactly the same, no drivers had to be installed started right up so thats enough of the applause to the programmers.
[B]
The Problem:[/B]

Now everything works except when I try to play a video I don't see or hear anything. No I go to youtube i can see videos there. I can play music and everything else. Just can't watch any videos on my computer. Now I do not know what my video card is, as I said before took out of one of the computers I was working with. Nothing was on it either so I am not sure. I hope someone can help me.

---

### Post by nhasian on 2008-11-05
probably just the video codecs.  try playing your videos with vlc.

```
sudo apt-get install vlc
```

---

### Post by hack13 on 2008-11-05
Yes. I have tried VLC Player. That was my first own trouble shoot. I don't understand. It acts like it is playing but i see nothing and hear nothing.

---

### Post by hack13 on 2008-11-05
I can hear video sound now just can't see it. I am using VLC Player and can hear the sound but can't see. I have tried different Deinterlace modes none show me video.

---

### Post by stoogiebuncho on 2008-11-06
Have you tried installing medibuntu?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Medibuntu allows Ubuntu to play a lot of the restricted file formats.

As for watching youtube videos, you need flash.  Go here:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Download the .deb file.  When you've got it, double-click to install.

---

### Post by Yojimbo. on 2008-11-06
You sure your drivers were installed correctly?

---

### Post by hictio on 2008-11-06
What version of Ubuntu are you running?
What videos did you try to watch?

For instance, on Intrepid, on your Home Folder, there is another directory called "Examples", inside, there is another one, called "Ubuntu_Free_Culture_Showcase", inside, there is a sample video, called "StopMotionUbuntu.ogv".
If you go to that directory, and click on the video, does it play at all?

---

### Post by Redhishan on 2008-11-06
Hi,

Go to the add/remove programs, show: all available app then type mp3 in  search and wait. A list will appear with GStreamer ffmpeg codec and its extra plugins, select them and apply... Its surely due to missing plugins...

Try it and please let me know...

---

### Post by hack13 on 2008-11-06
> **stoogiebuncho said:**
> Have you tried installing medibuntu?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Medibuntu allows Ubuntu to play a lot of the restricted file formats.

As for watching youtube videos, you need flash.  Go here:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Download the .deb file.  When you've got it, double-click to install.

Thank you the Medibuntu worked. I can watch my videos again.:KS

---

