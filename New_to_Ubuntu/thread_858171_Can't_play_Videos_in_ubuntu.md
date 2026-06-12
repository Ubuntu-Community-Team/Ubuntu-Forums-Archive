---
title: "Can't play Videos in ubuntu"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by jamil_1 on 2008-07-13
I am having problem in play videos in ubuntu. I have Intel graphics card 945G 
with shard memory of 128 MB. Whenever I try to play a video with a media player it starts the audio and then crashes. Only mplayer continues to play but it doesn't play video--plays only sound.

My Mplayer output can be found at: [http://paste.ubuntu.com/27071/](http://paste.ubuntu.com/27071/)
And lspci scan at: [http://paste.ubuntu.com/27013/](http://paste.ubuntu.com/27013/)

---

### Post by bumanie on 2008-07-13
Follow this guide to enable multi-media support/codecs [http://www.medibuntu.org/](http://www.medibuntu.org/) Also I suggest installing vlc player which plays almost every known codec. > sudo apt-get install vlcin terminal. Could also do > sudo apt-get install restricted-extras

---

### Post by jamil_1 on 2008-07-13
I have tried vlc player. It does play videos but when I go into full screen mode it makes the video as of very low resolution. I suspect the issue is with display driver.

---

