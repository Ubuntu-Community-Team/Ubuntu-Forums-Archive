---
title: "[SOLVED] external hardrive"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by haZZe08 on 2008-07-15
i have a maxtor external hardive. When I try and play my movies it plays without any sound and my music does the same thing. It plays, but no sound. I can view videos in youtube with sound. What do I need to be able to view(some of my pron movies won't stream; i get an error(com%50))and get sound outta my external?

on hardy

---

### Post by pi.boy.travis on 2008-07-15
Try right clicking on the sound icon in the notification area and selecting open volume control, and check all the sliders in the playback tab.

You could also go to a terminal ans type alsamixer.

Hope this helps!

---

### Post by haZZe08 on 2008-07-15
yea, checked it. NO dice tho. thanx

---

### Post by Sydius on 2008-07-15
Is it only the movies on the external hard drive that have this issue, or does it not work for any local file?

---

### Post by haZZe08 on 2008-07-15
only movies and music outta my external. What do you mean by any local file?

---

### Post by stalkier on 2008-07-15
> **haZZe08 said:**
> only movies and music outta my external. What do you mean by any local file?

Local means on the main hdd, not the external. try copying a small file and then playing it. Do one video and one mp3.

---

### Post by haZZe08 on 2008-07-15
still no sound.

---

### Post by pi.boy.travis on 2008-07-15
What kind of files are we talking about here?  mp3, ogg, flac, etc.

---

### Post by StrawberryJam8 on 2008-07-15
What kind of file types are they? Can you copy paste them to your main drive and see if they work. Have you tried running other different music or video files from your main drive? Are they playing well? Do they have sound?

Since you can hear music from Youtube, It's probably safe to assume that your player or the video file is incompatible. otherwise I'd start thinking you recorded the video on mute.

---

### Post by webofunni on 2008-07-15
Hi haZZe08,

  Are you getting sound for : 

```
speaker-test
```

If no give the results of : 

```
lspci
 aplay -l
lsmod

```

---

### Post by haZZe08 on 2008-07-15
mp3, xvid, avi...

i downloaded them all using windows. If I transfer them to my main drive it plays but no sound. I've tried using mplayer, realplayer and vlc but still get the same issue.

i ran the speaker test and I get static sound(which I suppose thats what i'm supposed to here)
 and it gave me this 

speaker-test 1.0.15

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 2048 to 16384
Period size range from 1024 to 1024
Using max buffer size 16384
Periods = 4
was set period_size = 1024
was set buffer_size = 16384
 0 - Front Left
Time per period = 2.661683
 0 - Front Left
Time per period = 2.986275

---

### Post by haZZe08 on 2008-07-15
i'm downloading harold and kumar go to white castle using the bit torrent on hardy. Hopefully i get sound when its done. COuld it be that since I downloaded my media using windows that it just doesnt play on linux?

---

### Post by pi.boy.travis on 2008-07-15
Where you prompted to download any additional packages?  Most Linux distros, Ubuntu included, need extra packages that can't be legally included with the OS to play proprietary formats.  I quote from the documentation:

To install extra codecs, press Applications &#9656; Add/Remove..., type &#8220;codec&#8221; in the Search box and select which codecs you want to install. Press Apply to install the selected codecs.

			

In some countries, the use of certain codecs may be prohibited by law. You should verify that you are permitted to use them before installing them.


Hope this helps!

---

### Post by haZZe08 on 2008-07-16
> **pi.boy.travis said:**
> Where you prompted to download any additional packages?  Most Linux distros, Ubuntu included, need extra packages that can't be legally included with the OS to play proprietary formats.  I quote from the documentation:

To install extra codecs, press Applications &#9656; Add/Remove..., type “codec” in the Search box and select which codecs you want to install. Press Apply to install the selected codecs.

			

In some countries, the use of certain codecs may be prohibited by law. You should verify that you are permitted to use them before installing them.


Hope this helps!



i have gstreamer ffmpeg vid plugin and gstreamer dirac plugin enabled. BUt when i try to enable  xine extra plugin it says "xine extra plugins cannot be installed on your computer type (i386)

---

### Post by Pro-reason on 2008-07-16
Install codecs with the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repos.

```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring non-free-codecs

```

---

### Post by haZZe08 on 2008-07-16
> **Pro-reason said:**
> Install codecs with the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repos.

```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring non-free-codecs

```


i get this: HTTP request sent, awaiting response... 510 Not Extended
23:04:43 ERROR 510: Not Extended.

---

### Post by haZZe08 on 2008-07-16
wait, i ran the commands again and it did something

it gave me this :  sudo apt-get update && sudo apt-get install medibuntu-keyring non-free-codecs

pressed enter and that was it, but I still get no sound

---

### Post by mc4man on 2008-07-16
Many times no sound _may be resolved_ as here (not just for 5.1)
[http://ubuntuforums.org/showthread.php?p=5388815#post5388815](http://ubuntuforums.org/showthread.php?p=5388815#post5388815)

If the medibuntu repo hasn't been added using wget (the site as had recent issues) read the edit here
[http://ubuntuforums.org/showthread.php?p=5182809#post5182809](http://ubuntuforums.org/showthread.php?p=5182809#post5182809)

---

### Post by haZZe08 on 2008-07-17
> **mc4man said:**
> Many times no sound _may be resolved_ as here (not just for 5.1)
[http://ubuntuforums.org/showthread.php?p=5388815#post5388815](http://ubuntuforums.org/showthread.php?p=5388815#post5388815)

If the medibuntu repo hasn't been added using wget (the site as had recent issues) read the edit here
[http://ubuntuforums.org/showthread.php?p=5182809#post5182809](http://ubuntuforums.org/showthread.php?p=5182809#post5182809)


sweet I got my sound working now. Just like you said. system>pref>sound then change the auto detect. thanx homie. can close this thread now

---

