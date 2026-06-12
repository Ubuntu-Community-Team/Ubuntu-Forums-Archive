---
title: "Alternatives to Itunes"
date: 2014-03-10
forum: New to Ubuntu
---

### Post by sdvf on 2014-03-10
Hi. What are the alternatives of itunes for Linux? I need it to sync songs with my ipod.

Tks

---

### Post by Tristan_Williams on 2014-03-10
Amarok - Amazing
Banshee - Almost as amazing
Rhythmbox - About as amazing as Banshee
Clementine - Does its job
Gtkpod - Does its job

Your best bet is Amarok.

In order for any of these to work you need to install "libimobiledevice"
```

sudo apt-get install libimobiledevice4 libimobiledevice-utils

```

---

### Post by sdvf on 2014-03-10
I have Clementine but i can't manage my music list of ipod. It recognize the divice but only charge battery.

---

### Post by jaspreet on 2014-03-10
Just wondering, amarok vs rythembox, which one would be better?

---

### Post by Tristan_Williams on 2014-03-10
For Ipod, definitely Amarok. It is more fully featured.
Don't get me wrong, Rhytmbox is amazing too, but Amarok is just better

---

### Post by sdvf on 2014-03-12
OK, i've got amarok, but there's a little problem. None of my songs works there. I've got more than 60GB of music and i cant play even one on amarok. 

"download of charts seems to have failed. Please check your internet conection"

"Time expired access on server 207.200 something....."

That's the massages i got when i open the program.

---

### Post by sdvf on 2014-03-12
> **sdvf said:**
> OK, i've got amarok, but there's a little problem. None of my songs works there. I've got more than 60GB of music and i cant play even one on amarok. 

"download of charts seems to have failed. Please check your internet conection"

"Time expired access on server 207.200 something....."

That's the massages i got when i open the program.
Help?

---

### Post by monkeybrain20122 on 2014-03-12
I don't use any Apple product, but from what I read iPod support is kind of hit and miss depending on which model. So to get help you would need to be more specific.

Since Apple doesn't support Linux, iPod support on this platform is the result of third party hack. So I would simply not use an iPod, problem solved.

---

### Post by andrew.46 on 2014-04-20
> **sdvf said:**
> OK, i've got amarok, but there's a little problem. None of my songs works there. I've got more than 60GB of music and i cant play even one on amarok.

Amarok uses gstreamer for playback and for some playback you will need the ugly, bad and ffmpeg/libav versions.

---

### Post by andrew.46 on 2014-04-20
> **sdvf said:**
> 
"download of charts seems to have failed. Please check your internet conection"

"Time expired access on server 207.200 something....."

That's the massages i got when i open the program.

For this one simply uncheck the script to stop it running. Have a look at: Settings --> Configure Amarok --> Scripts --> Scriptable Services --> 'Free Music Charts. Listen to the Darkerradio.com Free Music Charts.'

---

### Post by mstutson on 2014-04-29
Question? I have Gnome and I have a movie on Itunes. I want to get that movie and bring it to my system. Is it possable and how do I do it.

---

