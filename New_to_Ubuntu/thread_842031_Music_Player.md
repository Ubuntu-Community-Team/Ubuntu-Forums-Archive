---
title: "Music Player"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by dinomite89 on 2008-06-27
Hey,

After painstakingly installing all relevent codecs i have imported all my music into rythem box, but i click on the file and it says 

"missing element ffmpegcolourspace check your GStreamer instillation"

on every file!!!!!!!!!!

Please Help

Out.

---

### Post by rburkartjo on 2008-06-27
din, try this go to applications add/remove then when search box comes up type in banshee. this is in my opinion the best music player and it should have no problem in finding and installing all the music you have on your hard drive. i think it is cool. just my 2cents and easy to use/cheesemaker
note banshee will be under sound and videos after you install

---

### Post by Xiong Chiamiov on 2008-06-27
Recommending banshee is fine, but he *did* ask for help with fixing rhythmbox, not replacing it.

@OP:
Do you have the package gstreamer0.10-ffmpeg installed?

You might try looking through [this thread]("http://ubuntuforums.org/showthread.php?t=766683").

---

### Post by dinomite89 on 2008-06-27
rburkartjo,

banshee does not show up in my add/remove programs, im running 8.04 Hardy, although any otehr suggestions would be great

Out.

---

### Post by Papenco on 2008-06-27
Open Synaptic package Manager and search for Gstreamer to see if it is installed.

If it's not, install it; if it is installed, try reinstalling Rhythmbox.

Open a Terminal and type
```

sudo apt-get purge rhythmbox

```
```
sudo apt-get install rhythmbox
```

If that didn't work and you still want to try with banshee

Open a Terminal 

```
sudo apt-get install banshee

```

---

