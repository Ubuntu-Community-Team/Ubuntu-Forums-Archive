---
title: "[SOLVED] How do I convert .ogg files to simpler files."
date: 2008-08-15
forum: New to Ubuntu
---

### Post by LeetSpeak on 2008-08-15
Hey guys, I recently just downloaded the recordmydesktop program and I recorded what Linux can do with all these amazing features it comes with. Did it to show it to my friend ( He's thinking of changing to Linux as well ) But his computer doesn't read .ogg files, is there anyway I can convert .ogg files to something all computers can read easily? He has a MAC. Orrr, is there anyway I can convert the .ogg file to something Photobucket reads, it's funny how it can upload everything BUT .ogg files,

Thanks in advance :)

---

### Post by jualin on 2008-08-15
You can install [this on the MAC]("http://www.vorbis.com/setup_osx/") and it should read ogg files just fine. If not there is a program called Convertit that works just fine. [Here is a thread of how to install Convert it]("http://ubuntuforums.org/showthread.php?t=567016")

---

### Post by tahina on 2008-08-15
Apparently vlc media player can convert files: [http://maketecheasier.com/convert-ogg-to-mp4-using-vlc-media-player/2008/02/18](http://maketecheasier.com/convert-ogg-to-mp4-using-vlc-media-player/2008/02/18)

---

### Post by jualin on 2008-08-15
Wow, I didn't know that VLC was so amazing. Thanks dude!

---

### Post by eggdeng on 2008-08-15
The simplest way, assuming you already have ffmpeg is
```
ffmpeg -i inputfile.ogg outputfile.avi
```
For inputfile, read /path_to_file/filename, likewise for outputfile.
If you don't have ffmpg
```
sudo apt-get install ffmpeg
```

---

### Post by LeetSpeak on 2008-08-15
Wow the VLC worked, didn't know VLC converts, I thought it just reads .vlc videos. Thanks guys!

---

### Post by LeetSpeak on 2008-08-15
Signature Test

---

