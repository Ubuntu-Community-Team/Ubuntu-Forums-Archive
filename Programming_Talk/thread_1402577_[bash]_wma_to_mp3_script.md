---
title: "[bash] wma to mp3 script"
date: 2010-02-09
forum: Programming Talk
---

### Post by M4rotku on 2010-02-09
hey guys,

I tried adapting a bash script that I found on another forum.  It's supposed to convert wma's to mp3's, but I adapted it to try and get the mp3's in a better quality.  When I try to run the script, I get the error:  "unexpected end of file."  I don't know anything about bash, but I know python and C++.  Can anyone tell me what I'm doing wrong?  It's probably something very basic.

[PHP]#!/bin/bash

current_directory=$( pwd )

#remove spaces
for i in *.wma; do mv "$i" `echo $i | tr ' ' '_'`; done

#remove uppercase
for i in *.[Ww][Mm][Aa]; do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`; done

#Rip with Mplayer / encode with LAME
for track in *.wma ; do ffmpeg -y -i "$track" -f wav - | lame --cbr -b 320 - "$track.mp3"

#convert file names
for i in *.wma; do mv "$i" "`basename "$i" .wma`.mp3"; done

rm audiodump.wav done[/PHP]

Much thanks,
M4rotku

---

### Post by sharpdust on 2010-02-09
> **M4rotku said:**
> hey guys,

I tried adapting a bash script that I found on another forum.  It's supposed to convert wma's to mp3's, but I adapted it to try and get the mp3's in a better quality.  When I try to run the script, I get the error:  "unexpected end of file."  I don't know anything about bash, but I know python and C++.  Can anyone tell me what I'm doing wrong?  It's probably something very basic.

[PHP]#!/bin/bash

current_directory=$( pwd )

#remove spaces
for i in *.wma; do mv "$i" `echo $i | tr ' ' '_'`; done

#remove uppercase
for i in *.[Ww][Mm][Aa]; do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`; done

#Rip with Mplayer / encode with LAME
for track in *.wma ; do ffmpeg -y -i "$track" -f wav - | lame --cbr -b 320 - "$track.mp3"

#convert file names
for i in *.wma; do mv "$i" "`basename "$i" .wma`.mp3"; done

rm audiodump.wav done[/PHP]

Much thanks,
M4rotku


Hello the last 'done' is at the wrong position.
It should be moved to after "track.mp3". Here is the script again better formatted:

```
#!/bin/bash

current_directory=$( pwd )

#remove spaces
for i in *.wma; do
  mv "$i" `echo $i | tr ' ' '_'`;
done

#remove uppercase
for i in *.[Ww][Mm][Aa]; do 
  mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`;
done

#Rip with Mplayer / encode with LAME
for track in *.wma; do
  ffmpeg -y -i "$track" -f wav - | lame --cbr -b 320 - "$track.mp3"
done

#convert file names
for i in *.wma; do
  mv "$i" "`basename "$i" .wma`.mp3";
done

rm audiodump.wav
```

I have not validated that it works correctly since I don't have ffmpeg or lame installed, but it should get passed your previous error.

---

### Post by HarrisonNapper on 2010-02-09
Doesn't LAME stand for "LAME Ain't an MP3 Encoder"?

---

### Post by sharpdust on 2010-02-09
> **HarrisonNapper said:**
> Doesn't LAME stand for "LAME Ain't an MP3 Encoder"?

Yes, it does.

---

### Post by cascade9 on 2010-02-09
> **M4rotku said:**
> I tried adapting a bash script that I found on another forum.  It's supposed to convert wma's to mp3's, but I adapted it to try and get the mp3's in a better quality.  When I try to run the script, I get the error:  "unexpected end of file." 

Just so you know, converting to a bigger size mp3 (320K in this case) than the original source probably wont be any better than a slightly smaller file. Even converting 320K .wma to 320K .mp3 wont be as good as a CD-> 320K .mp3, and if your .wmas are smaller than 320K (which is 97.5%+ of all the wma files I've ever seen) your just wasting space. 

I'd probably convert to the same bitrate as the original file......if I was too cheap to buy the CD, or (and this has happened a lot to me) if the CD is out of print, and the .wma files are all I could find.

---

### Post by M4rotku on 2010-02-09
I have the wma files from back when I used to use windows.  Back then all of my music was in wma's.  I haven't kept all of the original cd's and such, b/c I always just had my music on my computer.  It wasn't an issue until I got my mp3 player, now I want all of the tracks in the same format.  I don't know anything about LAME, but that sounds like an accurate acronym.  I'll try the new script, thanks for your help.

---

### Post by HarrisonNapper on 2010-02-09
> **sharpdust said:**
> Yes, it does.

Ah, just looked it up. I've seen it before, but always assumed it didn't encode for MP3. Learn something new every day :D

---

