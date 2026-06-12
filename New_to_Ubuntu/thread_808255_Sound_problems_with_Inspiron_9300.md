---
title: "Sound problems with Inspiron 9300"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by CrossS on 2008-05-26
Hi

I have just installed Ubuntu 8.04 on my Inspiron 9300 and I'm experiencing problems with the sound. I have never used Linux before so I'm a complete noob :/

There are three speakers on my laptop, two speakers in front and a sub underneath the computer. There isn't coming any sound at all (as far as I can hear) from the front speakers, only form the sub. But the sound from the sub ain't just bass it sounds like everything has been blended together and the computer does not recognized witch sounds should come out from the designated speaker and when everything comes out of just the sub speaker is just muffled and the quality is crappy.

When I boot my computer in windows the sound works as it should do.

If anyone has any advice in this area it would sorely appreciated!

---

### Post by Inxsible on 2008-05-26
Lets start with the very basic.Open up a terminal (Applications>>Accessories>>Terminal) and type in this command```
alsamixer
``` Max all the volume levels there and see if that works. When something says MM - it means that its muted. You can click M to unmute it and up and down arrows to increase or decrease volume levels.

---

### Post by CrossS on 2008-05-26
When I set all on the same level and connected Master, Master M and PCM to the volume buttons on my computer through System -> Preference -> Sound, under Default Mixer Tracks it got much better, now the sound is coming out of correct speakers but there the quality is still a little of when I stream music form different internet sites. It might be the internet sites I try but.. Sounds are difficult to explain. 

It's difficult to know because the only program where mp3's are starting is VLC, it's playing but without sounds :/ amarok is just frezing and the rhythembox music player don't have the correct codecs.

I'm in deep water now.

---

### Post by Inxsible on 2008-05-26
Applications>>Add/Remove. Search for "gstreamer" without the quotes and install all of them. See if that makes any difference to the quality.

---

### Post by CrossS on 2008-05-26
Now I have installed all of them. But it is still difficult to know when I can't get any of the programs I have in Ubuntu to play music of xvid files. Do you know how to get sound in vlc or/and to get rhythmbox music player and amarok to work?
In Rhythmbox nothing starts (like its paused, and yes I have tried pressing play:) ) and amarok just freezes. VLC plays videos and mp3's but there is no sound.

Streaming works very well

Thx so much for helping me

---

### Post by CrossS on 2008-05-26
Never mind. When I closed Firefox all the programs started to work. Don't know what the problem was but as long as it works I'm happy :D

Thx again. You saved my day!

---

