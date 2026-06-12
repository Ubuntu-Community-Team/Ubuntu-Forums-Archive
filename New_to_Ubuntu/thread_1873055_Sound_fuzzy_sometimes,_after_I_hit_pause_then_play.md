---
title: "Sound fuzzy sometimes, after I hit pause then play the music plays fine"
date: 2011-10-31
forum: New to Ubuntu
---

### Post by venom104 on 2011-10-31
Can anyone help me out with this? Sometimes when I play an mp3, the sound that comes out of the speakers is a HORRID scratching fuzzy noise, yet the music is playing as well. If I hit pause, then play, the song plays perfectly.

I'm playing my songs with VLC, I've never had this problem before with any previous version of VLC (windows or ubuntu) or ubuntu version.

I am using ubuntu 11.10 with the KDE plasma desktop.

---

### Post by venom104 on 2011-11-03
I found the problem. After switching my decoder backend to xine and having the same problem, I determined that it wasn't the decoder. The problem was VLC. I don't know how it went past the initial testing phase, but it appears the default VLC package (if not including the stuff you build from source) has some type of bug that causes sound distortion on almost all media when you open a file (first time only) upon logging into a session.

SOLUTION: I went around it and installed the xine backend to totem and started using totem.

---

