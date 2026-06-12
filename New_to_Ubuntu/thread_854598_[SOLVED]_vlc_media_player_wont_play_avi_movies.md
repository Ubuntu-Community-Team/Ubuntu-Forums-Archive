---
title: "[SOLVED] vlc media player wont play avi movies"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by workshop1702 on 2008-07-09
hi i am having major problems getting any movie player to play avi movies , have tried all the recomendations on codecs etc but non have worked, could someone point me in the correct dirrection please, how doi get it to play avi and what codecs do i need. Thanks Andrew

---

### Post by bobnutfield on 2008-07-09
VLC plays just about everything you can throw at it.  What errors are you getting?  Try openindg VLC from the command line and see what the errors say when you try to play a file.

Bob

By the way, the newest version of VLC requires ffmpeg (available from the medibunty repos.  Also, while this thread isn't specifically about AVI files, if you follow it, you can play anything.

[http://ubuntuforums.org/showthread.php?t=661833&highlight=commercial+dvd]("http://ubuntuforums.org/showthread.php?t=661833&highlight=commercial+dvd")

---

### Post by workshop1702 on 2008-07-09
hi again one of my avi downloads has played ok the ones that wont play have divx or xvid infront of the avi do i need some special codec to play these please. thanks again for any help . Andrew

---

### Post by tjwoosta on 2008-07-09
first enable the medibuntu repository (everthing is here)
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

then do

```
sudo apt-get install ubuntu-restricted-extras
```

then 

```
sudo apt-get install w32codecs
``` (w64codecs for 64bit ubuntu)

that should cover every codec you can think of

---

### Post by workshop1702 on 2008-07-16
have managed to play a couple of the divx avi downloads but most of them still will not play . anyone any more ideas please

---

### Post by RomeReactor on 2008-07-16
Hi. Have you enabled the Medibuntu repository and installed the packages tjwoosta suggested? Have you tried opening the files in another aplication--Totem, Mplayer? Are you sure the files are not corrupt?

---

