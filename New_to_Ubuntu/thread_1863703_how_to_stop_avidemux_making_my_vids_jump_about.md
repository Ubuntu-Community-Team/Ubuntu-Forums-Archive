---
title: "how to stop avidemux making my vids jump about"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by tommyleeds on 2011-10-18
hi
im using avidemux to convert mpeg's to avi's
they work in ubuntu just great but when i play them on my friends windows computer the video jumps about when theres a scene change
im on ubuntu 11.04
can any body help me ?

---

### Post by trozamon on 2011-10-18
I don't know if avidemux has problems, but I use ffmpeg and it works flawlessly.

---

### Post by tommyleeds on 2011-10-18
cheers trozamon i will try ffmpeg

---

### Post by tommyleeds on 2011-10-19
have tried ffmpeg but i dont like terminal programmes coz im a ubuntu noobie
can some body help me fix the avidemux problem ?
when the video change scenes you can still see the last scene jump up

---

### Post by trozamon on 2011-10-19
FFMpeg is actually quite easy: 
```
 ffmpeg input_vid.sample output_vid.convert 
```FFMpeg guesses how to convert it based on the file extension of the output video, so it's not too difficult.

---

### Post by tommyleeds on 2011-10-21
cheers trozamon you make it look real easy......i will try it out :)

i still want to fix the avidemux problem......does any body know how to fix it ?

---

