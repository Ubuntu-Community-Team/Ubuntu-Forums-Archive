---
title: "Music/Media players crashing constantly"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by Toitovna on 2012-07-26
Hi there,

I just bought a new computer, which came without any operating system. I installed Ubuntu 12.04 from a USB onto the hard drive and it seemed to be working perfectly fine.

Except when I went to put music on, Rhythmbox, then Banshee, then Clementine and now gmusicbrowser have all failed to play any songs from the few albums I put on the desktop. They all manage to load the music onto the library but whenever I click "play" they all go grey and I have to force close. What could possibly be the problem? Is there some driver or something I need to install?

The same thing happens when I try to play a video over my network using VLC, which has always been reliable for me in the past, though I'm not sure if the video problem is the same or unrelated? Either way these are pretty basic functions that are currently totally bombing.

thanks

---

### Post by jmfal on 2012-07-26
Welcome to Ubuntu  Forums

Try installing  ubuntu restricted extras, it supports many audio formats, it's in the software center, synaptic or using the terminal
```
  sudo apt-get install ubuntu-restricted-extras    
```

You may still have  audio problems this will eliminate one.

---

### Post by Toitovna on 2012-07-26
There hasn't been any change...

I'm only very new to Linux, but surely there shouldn't be too much that you have to do before music programs will play .mp3's and video programs will play .avi's and .mp4's? Do you think that there was a glitch when I installed it or something, for so many things to go wrong at once?

---

### Post by jmfal on 2012-07-26
Check out the alsamixer link below
Make sure all speaker controls are not muted

---

### Post by Toitovna on 2012-07-26
I don't think it's a problem in terms of the sound itself - the programs simply crash before any sound has a chance to come out of the speakers. The music players all freeze up & go grey and ask me to force quit. VLC doesn't really do anything, it just sits there with the video time length but without actually playing anything, I can close it without it freezing.

Is this an uncommon problem to be experiencing?

---

