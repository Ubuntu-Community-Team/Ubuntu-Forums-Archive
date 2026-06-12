---
title: "Winff"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by ozbolt on 2008-10-11
Never worked and now i would really need it.
Here is reason:
[[img]http://shrani.si/t/1O/ri/4Vg03b6v/screenshot-2.jpg[/img]](http://shrani.si/?1O/ri/4Vg03b6v/screenshot-2.png)
I have all the codecs from add/remove installed (gstreamer) so all the videos do work. Just converting... Anly workable in Windows so please make it possible in Linux. Witch codecs to install?

---

### Post by whitethorn on 2008-10-11
It looks like your missing the xvid codec. I'm not quite sure what package you need though.

---

### Post by ozbolt on 2008-10-12
This does for every movie I try to convert - or aac is missing or xvid is mising etc. What codec??

---

### Post by hyper_ch on 2008-10-12
try vlc to watch it

---

### Post by ozbolt on 2008-10-12
VLC works and have installed so no problem with that, as I said watching works, also converting with soundconverter (mp3 to ogg or reverse) works, just Winff does not see codecs in my system or I don't have installed those WinFF needs.
Thanks for help and every answer.

---

### Post by MrWES on 2008-10-12
You need to install the nonfree version of ffmeg from mediabuntu respositories:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Bill

---

### Post by ozbolt on 2008-10-12
Still same after updating and upgrading and reinstalling winff and ffmpeg. More suggestions?

---

### Post by whitethorn on 2008-10-12
I don't know if this will help, but I've read somewhere that mplayer and winff kinda use the same codecs.  I'm not sure, but it can't hurt to try.  Download this package unpack it and copy/move it to /usr/lib/codecs/  

[http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2](http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2)

then see if winff works.

---

### Post by MrWES on 2008-10-12
Do a complete removal of ffmeg and then reinstall to make sure you only using the nonfree version.

Bill

---

### Post by ozbolt on 2008-10-12
Thank YOU. Now I am only searching for right one to work on my Wievty (LG KU990) and then I am step closer to 100% adoption to Linux. Gracias, Danke, Hvala!

---

