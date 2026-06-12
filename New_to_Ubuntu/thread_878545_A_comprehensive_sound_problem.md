---
title: "A comprehensive sound problem"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by WonderStivi on 2008-08-03
I have encountered a quite disturbing sound problem for the 2nd time after converting my HTPC over to Ubuntu+XBMC.

I'm using a EVGA 680i motherboards' onboard SPDIF (ALC885).

Yesterday I was attempting to play an iso in XBMC, which made it hang. I killed the gnome session and logged back in. After that, there's been no sound in Ubuntu at all, and in XBMC there's only sound from movies that's encoded with Dolby Digital or DTS. If I play an mp3 or a movie with stereo only, there's no sound.

I have no idea how to fix this, and I'd rather not reinstall Ubuntu for the 3rd time to fix the problem. I've been going through sound options and alsamixer, and everything looks sweet. But still no sound.

Hopefully someone here can help me.

In advance,

thanks.

---

### Post by WonderStivi on 2008-08-04
I ended up reinstalling Ubuntu. If anyone has a clue how to fix this problem, please post it here, as I'm sure it'll happen again :(

---

### Post by WonderStivi on 2008-08-04
It happened again. It has clearly something to do with XBMC, but I can't find anyone else having similar problems. I guess I will have to go back to using XP on my HTPC until someone with a bit (a lot) more knowledge than me gets bothered with the same bug.

Strange that it blocks all sound output from Ubuntu, while Dolby Digital and DTS works fine in XBMC.

---

### Post by Legio on 2008-08-09
I did have the exact same symptoms and i found the other channels to be muted.

Try the alsamixer and press m on each channel that is not on to turn it on (or off)

The DD probably goes through your SPDIF or TOSLINK as PCM, whereas the stereo does not. 

Hopes this simple solution works.

---

### Post by WonderStivi on 2008-08-11
I've tried it all in alsamixer, and none of the channels were muted. I haven't tried the jack-channels on the sound card, and it might be that it sends the audio to that channel when playing stereo.

Anyway, I've changed back to XP on my HTPC. For me, it has to work (at least close to) perfect every time, and with Linux/Ubuntu it just doesn't do that. I'll try again in half a year or so, to check if there's any change.

---

### Post by therealbrad on 2008-10-11
I've got this exact problem, too. Please tell me there's a way to get my sound back without reinstalling Ubuntu. I've uninstalled xbmc (I won't be trying that software again) but I still have no sound in Ubuntu except for AC3 passthrough.

---

### Post by Purple8 on 2009-04-03
Help I now have the exact same problem. i dont want to have to reinstall .

---

