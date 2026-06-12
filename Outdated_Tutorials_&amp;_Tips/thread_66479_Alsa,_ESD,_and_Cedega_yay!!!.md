---
title: "Alsa, ESD, and Cedega yay!!!"
date: 2005-09-17
forum: Outdated Tutorials &amp; Tips
---

### Post by KRavEN on 2005-09-17
Okay, I finally got this working after reading the multiple threads and a lot of googling.  There are currently 2 big threads for setting up sound in the forums.  Both are correct, but each is missing a couple things.  So heres how to get it working:

Follow steps 1 and 2 from [here](http://www.ubuntuforums.org/showpost.php?p=160497&postcount=1)  except use the asound.conf code from [here](http://www.ubuntuforums.org/showpost.php?p=230948&postcount=1). 

Then do step 3

Step 4 should is correct for gstreamer but Beep (BMP) must be set to ESD not Alsa or you will get horrible sound.

Next Open ~/.transgaming/config,
find the following line:

[WinMM]
and change the following lines to

[WinMM]
"Drivers" = "winealsa.drv"
;"WaveMapper" = "msacm.drv"
;"MidiMapper" = "midimap.drv"

then find [winealsa]
and change that section to:

[winealsa]
"UseMMap" = "Y"
"pcm0" = "dmixer"

The two last lines are the most important. Without those cedega will produce no sound.  

The trick everyone misses is the pcm0 because everything you find says to set it to default which will NOT work.  Some problem with cedega and alsa.

Any other app that will support ALSA may or may not work with default.  If it doesn't simply put dmixer instead and it will usually work.  If not, you can always send it to ESD.

Your luck with UseMMap under Hoary may vary but it works just fine with Breezy.

With this I can listen to my music and play WoW at the same time.  There is also a pretty sweet addon for wow call wTunes that uses perl scripts to control xmms from within the game.  It was very easy to copy the perl script for xmms and add a new one for Beep.  Support could be added in moments for any other sound application that can be controlled via the console as well.

I'll follow up with a post telling how to get sound coming out both my USB headset and my speakers at the same time.

If any other alsa experts are out there I'd really like to know how to take the output from any application and connect it to a virtual device that will then show up as another output  in the mixer.  For instance now there is Main volume, PCM, and PC Speaker.  I would like it so I can add one for say XMMS and then when I move the slider up and down it controls only the output from XMMS.

---

### Post by nickless on 2006-07-09
I get this error in cvscedega:
```
err:module:BUILTIN_LoadModule loaded .so but dll winealsa.drv still not found
```
using Xubuntu, how can I install this modul manually?

---

