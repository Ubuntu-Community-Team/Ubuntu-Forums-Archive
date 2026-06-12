---
title: "totem and vlc not playing flash or flv files.."
date: 2009-04-02
forum: Philippine Team
---

### Post by killer_d76 on 2009-04-02
i just installed hardy heron 8.04 on my friends asus, i just installed the recent flash player plug-in and we were able to view videos on youtube.. then i mentioned to her that she can grab the videos from youtube easily by going to the tmp folder.. but when we try to play the said file (flash-video or flv) using totem/movie player we get this error!.. patulong naman po. (napahiya tuloy ako hehehe :lolflag:  )

---

### Post by loell on 2009-04-02
sa totem, mukhang kailangan mo mag install ng ***gstreamer0.10-plugins-bad***.

---

### Post by killer_d76 on 2009-04-02
wow loell that was quick!.. i tried to install **gstreamer0.10-plugins-bad** using terminal and here's what i got.

```
Reading state information... Done
gstreamer0.10-plugins-bad is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.

```

and we still got the same error on Movie Player.

---

### Post by albinootje on 2009-04-02
> **killer_d76 said:**
> when we try to play the said file (flash-video or flv) using totem/movie player we get this error!

Perhaps a :
```

sudo apt-get install ubuntu-restricted-extras

```
helps.
And can you try smplayer or mplayer for playing it ?

---

### Post by killer_d76 on 2009-04-02
thanks for the quick reply guys.. installing it right now.

---

### Post by killer_d76 on 2009-04-02
installed ubuntu-restricted-extras and MPlayer as well but still no good!..
here's the error i got using MPlayer..

---

### Post by Fenris_rising on 2009-04-02
I have had trouble of late with mplayer and totem with formats that they had played fine before. Have you added the medibuntu repos to your source list? 

I ended up using SMplayer in the end which played all the file types I was having trouble with. You do need to go into it's preferences and set vid to x11 and audio to Alsa. Hope that helps

regards

Fenris

---

### Post by loell on 2009-04-02
ahhh! headbuts youtube!

[http://ubuntuforums.org/showthread.php?t=1103825]("http://ubuntuforums.org/showthread.php?t=1103825")

seems a new re-encoding algo?

---

### Post by killer_d76 on 2009-04-03
hhmmm... i tried downloading new video from YouTube and it played well on my Movie Player, Totem and VLC using my trusty old Intrepid, but i get the same error when i played the same file on the newly installed/updated Hardy Heron?!, can it be the update on the Ubuntu Software that is preventing me from viewing flv files?

---

### Post by Samhain13 on 2009-04-04
> **loell said:**
> seems a new re-encoding algo?

I suspected as much. The only solution I've found so far is to download through KeepVid. If the FLV still doesn't work, get the MP4.

---

