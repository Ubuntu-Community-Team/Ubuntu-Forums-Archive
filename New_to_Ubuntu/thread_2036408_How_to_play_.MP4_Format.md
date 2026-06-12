---
title: "How to play .MP4 Format"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by PhalanxSec on 2012-08-01
How do I play the .mp4 file formats in Ubuntu? I want to use Ubuntu exclusively but first I need to find out how to play my music and videos.

---

### Post by levlaz on 2012-08-01
Have you installed the restricted extra?

```
 sudo apt-get install ubuntu-restricted-extras 
```

---

### Post by PhalanxSec on 2012-08-01
> **levlaz said:**
> Have you installed the restricted extra?

```
 sudo apt-get install ubuntu-restricted-extras 
```

Is that all there is to it?

---

### Post by blade4 on 2012-08-01
There are two options for you here

1) The easier path : Get VLC 

              sudo apt-get install vlc 

2) If your ubuntu version is 11+ , then you'll need to get synaptic first : 

             sudo apt-get install synaptic 

then get all gstreamer0.10 plugins , just search "gstreamer0.10 "(without quotes) and choose reinstall/install option for the following : 

gstreamer0.10-ffmpeg
gstreamer0.10-tools
gstreamer0.10-nice
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-good
gstreamer0.10-x
gstreamer0.10-bad
gstreamer0.10-gnonlin

These were the plugins on my ubuntu lucid - there may be additional plugins required on your system but give these a try if you want .

Cheers

---

### Post by PhalanxSec on 2012-08-01
> **blade4 said:**
> There are two options for you here

1) The easier path : Get VLC 

              sudo apt-get install vlc 

2) If your ubuntu version is 11+ , then you'll need to get synaptic first : 

             sudo apt-get install synaptic 

then get all gstreamer0.10 plugins , just search "gstreamer0.10 "(without quotes) and choose reinstall/install option for the following : 

gstreamer0.10-ffmpeg
gstreamer0.10-tools
gstreamer0.10-nice
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-good
gstreamer0.10-x
gstreamer0.10-bad
gstreamer0.10-gnonlin

These were the plugins on my ubuntu lucid - there may be additional plugins required on your system but give these a try if you want .

Cheers

I have the latest version of Ubuntu, 12.04. Can I still just install VLC Media Player and do it just from that?

---

### Post by blade4 on 2012-08-01
> I have the latest version of Ubuntu, 12.04. Can I still just install VLC Media Player and do it just from that? 	

Yes you can , I put the 2nd option there in case you preferred totem  .

---

### Post by techvish81 on 2012-08-01
> **levlaz said:**
> Have you installed the restricted extra?

```
 sudo apt-get install ubuntu-restricted-extras 
```

this is the best option, put the above command in terminal,  give your password, it will install all the necessary packages for media playback. you will be able to play most formats.

---

### Post by uRock on 2012-08-01
> **PhalanxSec said:**
> I have the latest version of Ubuntu, 12.04. Can I still just install VLC Media Player and do it just from that?

VLC plays everything. ubuntu-restricted-extras will be required for opening media within Rhythmbox.

---

### Post by levlaz on 2012-08-01
> **PhalanxSec said:**
> Is that all there is to it?

:) 

Yes that is all there is too it.. despite the common misconception Linux can be very simple at times. ;)

---

### Post by Dawnbandit on 2012-08-02
I'd suggest VLC Media Player.

---

