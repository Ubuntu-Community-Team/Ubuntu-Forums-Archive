---
title: "File converter program?"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-05-01
Hi folks, 

Does anyone know of any program for ubuntu similar to superC for windows? superC for windows is a program that can convert pretty much any file format to almost any other file format.... I am using OggCovert right now but I was wondering if there was anything out there similar to superC, or even if there is a superC for linux. The reason I ask is because OggCovert can only do... well... OGG and OGV files. I need MP3/AVI files for my MP3 player. 

Thanks, 

-'Mage

EDIT: In particular I need a program that can do FLV files.

---

### Post by master5o1 on 2008-05-01
I am also wanting to know how to convert files. Especially OGV->MP4/AVI and AVI->MP4.

---

### Post by SunnyRabbiera on 2008-05-01
well for music you could use audacity to convert most of your stuff.
you can also try VLC

---

### Post by unbuntued on 2008-05-01
> **UnWarierMage224 said:**
> Hi folks, 

Does anyone know of any program for ubuntu similar to superC for windows? superC for windows is a program that can convert pretty much any file format to almost any other file format.... I am using OggCovert right now but I was wondering if there was anything out there similar to superC, or even if there is a superC for linux. The reason I ask is because OggCovert can only do... well... OGG and OGV files. I need MP3/AVI files for my MP3 player. 

Thanks, 

-'Mage

EDIT: In particular I need a program that can do FLV files.
A quick search in synaptic reveals the following packages for audio:
*nautilus-script-audio-convert* and *soundconverter*

Not sure for the video though.

---

### Post by herbster on 2008-05-01
Depends what you want to convert. For video/audio, ffmpeg should do it. I've used convert for images many times, see man convert.

Few ffmpeg examples: [http://www.bala-krishna.com/convert-video-files-to-flv-using-ffmpeg-command](http://www.bala-krishna.com/convert-video-files-to-flv-using-ffmpeg-command)

I just used this yesterday:

```
ffmpeg -i youtubevideo.flv -f mp3 song.mp3
```

---

### Post by mmb1 on 2008-05-01
For basic sound file format conversion, I reccomend "sound converter," it's quite good and is available through synaptic.

---

### Post by oliviacond on 2008-05-01
> **mmb1 said:**
> For basic sound file format conversion, I reccomend "sound converter," it's quite good and is available through synaptic.
 
and remember to install gstreamer (ugly, bad, ffmpeg)

---

### Post by teamcoltra on 2009-04-14
Not wanting to gravedig but my favorite file conversion website is [http://www.zamzar.com](http://www.zamzar.com) I also use VLC on a few things as well.. but only if I am having issues with zamzar.

---

### Post by Eisenwinter on 2009-04-14
ffmpeg, mencoder.

---

### Post by perspectoff on 2009-05-02
> **oliviacond said:**
> and remember to install gstreamer (ugly, bad, ffmpeg)

You are misguided, my friend. FFMPEG can convert anything. You have to RTFM, of course. Linux is great, but it is not magic, and Jedi mind tricks do not yet work as an interface.

---

### Post by Paqman on 2009-05-02
> **unbuntued said:**
> 
Not sure for the video though.

Handbrake is a good universal solution. Once you've set up the presets to match your device it's pretty straightforward, and it's multithreaded which is a bonus.

Of course, there are other dedicated packages for specific devices, such as Iriverter, which makes converting video for Irivers, Creative Zen/Zen Vision:M, etc very simple. Have a search in Synaptic under your device name and see what pops up.

---

### Post by Volt9000 on 2009-05-02
What about [SoX](http://sox.sourceforge.net/)? It's command-line but works quite well, supports a plethora of file formats and you can even use it to apply effects to your sound files.

It's available in the repos.

```

sudo apt-get install sox

```

---

