---
title: "Playing video help"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by whojspurl on 2008-11-24
I just started using Ubuntu tonight. I'm using Limewire, but I can't watch the videos that I have downloaded. Is there a specific media player I should download? Or can I just not watch them at all?

---

### Post by phidia on 2008-11-25
You can try opening them by double clicking them that should start mplayer. What video format are the files in?
Normally codecs are not installed so the system will ask you if you want to install those.

---

### Post by Bucky Ball on 2008-11-25
Also, in Synaptics, you can install:

ubuntu-restricted-extras

That should fix things.

---

### Post by whojspurl on 2008-11-25
The videos that I have are the .mpg format. I tried double-clicking and I get an error message that says: Limewire could not launch the specified file. Executed command: xine/home/justin/limewire/saved/the.dark.knight.2008.mpg.

---

### Post by SuperSonic4 on 2008-11-25
I'm not sure if Limewire can do it directly, what happens if you navigate to the location and click to open.

Add the medibuntu sources:
```

sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```


```
sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs 
```

```
sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 vlc
```

The comprehensive guide is an excellent tool: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I've had no problems when following that guide

---

### Post by nhasian on 2008-11-25
VLC plays just about any kind of media file you can throw at it.

```
sudo apt-get install vlc
```

---

### Post by Bucky Ball on 2008-11-25
**System->Administration->Synaptic Package Manager**

Search for:

**ubuntu-restricted-extras**

Install.

If you installed tonight, there are some basic things you should do right now, before attempting to watch a video. This is the first. You may not even have drivers installed for your video hardware yet!

---

### Post by Olivier2371 on 2008-11-25
Sorry to drop in,

limewire video playback is only used under windows.

You could try to change the prefered player that limewire use,
in the preference window.

---

