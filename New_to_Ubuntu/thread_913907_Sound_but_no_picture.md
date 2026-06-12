---
title: "Sound but no picture"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by audreymac on 2008-09-08
I have succeeded in getting sound from RealPlayer and Totem.
Problem now:  A .avi XVID MPEG-4 video which I want to watch/record to disc but on Totem I only get sound, the screen is filled with lines of red dots.
I installed all the multimedia packages as per UBUNTU but was unable to locate w32 codecs in repository....
Can anyone advise please?
Thanks. amac

---

### Post by MegaJim on 2008-09-08
Do you have restricted by copyright repository enabled (multiverse)?

---

### Post by audreymac on 2008-09-08
software restricted by copyright or legal issues (multiverse) is listed under UBUNTU SOFTWARE.....
HOW DO I enable it?

---

### Post by aloshbennett on 2008-09-08
You can get it from medibuntu repositories

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by MegaJim on 2008-09-08
try installing the ubuntu-restricted-extras package by following the instructions here: [http://www.psychocats.net/ubuntu/nonfree](http://www.psychocats.net/ubuntu/nonfree)

If its still not working there might be a rendering problem - the best way to check is to disable any effects you have in the desktop (beryl/compiz etc.) and try playing with vlc in software - open up your file in vlc media player and enable an effect.

settings -> extended gui -> click enable image adjustment

---

### Post by audreymac on 2008-09-08
What do I type in the search box?
I tried a download from the listing via main server and an error message came up could not fetch http etc medibuntu packages
check your network connection and ensure the repository address is correct in preferences?????

---

### Post by MegaJim on 2008-09-08
What are you trying to do?

---

### Post by audreymac on 2008-09-08
I am trying to enable mediaubuntu for the restricted packages.  I tried the sudo command but still no picture....
VLU player is now operationing kinda - visualisations are working and audio.

---

### Post by MegaJim on 2008-09-08
You're going to have to be more specific than that; which instructions are you following, where did you get to, were there any error messages?

---

### Post by audreymac on 2008-09-08
Point taken.
I'll have to check.  At the moment when I try to play a avi video located on desktop - I get an error message avi file broken.

---

### Post by audreymac on 2008-09-08
Message displays:
blue heading :AVI INDEX
This AVI file is broken. Seeking will not work correctly. Do you want to repair it (this might take a long time)?
When I press NO - I get the video playing , small image centred on black screen but it stops playing after about 5 seconds.
This is a national geographic dvd.

---

### Post by audreymac on 2008-09-08
MegaJim, thanks for your patience and helpful links.
I can now play the dvd with MediaPlayer.
Picture is quite small and centred. How to fully extend the picture to a full screen?
amac

---

### Post by audreymac on 2008-09-15
My update4:
probs again with vision and sound.  Message reads -main error: decoder is leaking pictures, resetting the heap
main error: picture 0x85b1310 refcount is -1
main error: picture to date 0x85b141c has invalid status 6
main error: picture to display 0x85b141c has invalid status 6
main error: picture 0x85b141c refcount is -1
main warning: output date isn't PTS date, requesting resampling (98875)
main warning: buffer is 98391 late, triggering upsampling
main warning: PTS is out of range (-20058), dropping buffer
main warning: buffer is 65808 late, triggering upsampling
main warning: output date isn't PTS date, requesting resampling (182147)
main warning: audio drift is too big (247788), dropping buffer
main warning: audio drift is too big (215788), dropping buffer
main warning: audio drift is too big (183788), dropping buffer
main warning: audio drift is too big (151788), dropping buffer
main warning: timing screwed, stopping resampling
main warning: buffer is 119955 late, triggering upsampling
main warning: late picture skipped (102524)
main warning: late picture skipped (62572)
main warning: late picture skipped (22575)
main debug: decoded 103/104 pictures

---

