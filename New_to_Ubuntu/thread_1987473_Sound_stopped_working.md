---
title: "Sound stopped working"
date: 2012-05-26
forum: New to Ubuntu
---

### Post by bilboubu on 2012-05-26
XBMCbuntu

Sound had been working fine for months after identifying hw:0,7 as being the correct deviced and creating the appropriate asound file in my home folder. Now I am getting nothing.

alsamixer all are unmuted spdif options as before, aplay -l still lists the same as before, cant see anywhere else sound could have been muted.

As far as I am aware I had not made any updates, only installed a new version of xbmc. (I get no sound in xbmc or say youtube)

Since the issue I have updated to 12.04 to see if it would work again.

Is there anything obvious that could have caused this or something I can try.

aplay -D hw:0,7 tada.wav says sample format not available.

---

### Post by Hadaka on 2012-05-26
sounds like xbmc overwrote the codec settings. you could try ubuntu restricted
extras from the software center or better still, here is a link that seems to work
for just about any media player.
[http://ubuntuforums.org/showthread.php?t=1935072&highlight=libdvdcss&page=2](http://ubuntuforums.org/showthread.php?t=1935072&highlight=libdvdcss&page=2)
good luck.

---

