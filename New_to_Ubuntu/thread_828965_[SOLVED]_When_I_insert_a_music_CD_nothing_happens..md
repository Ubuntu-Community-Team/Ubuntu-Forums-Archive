---
title: "[SOLVED] When I insert a music CD nothing happens."
date: 2008-06-14
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-06-14
I thought that when you inserted a music CD in your drive that rhythmbox was suppose to startup.  Well when I do it the CD icon shows up on the desktop and thats all.  I have tried starting rhythmbox manually and tried to play the CD and it would not even recognize it.

---

### Post by Gannon8 on 2008-06-14
Did you burn the cd? If so did you burn it as a data cd? I never listen to music cd's so I don't know what happens.

---

### Post by alienexplorers on 2008-06-14
It was burnt as a music cd on a music cd disk.

---

### Post by Gannon8 on 2008-06-14
Could you try it in a different audio device, like a cd player, and see if that works?

---

### Post by alienexplorers on 2008-06-14
Yea, it works fine in my portable CD player.

---

### Post by forestpixie on 2008-06-14
How are they set up - open nautilus - Edit - Preferences - Media tab

---

### Post by alienexplorers on 2008-06-14
CD Audio --- open rhythmbox music player
Music Player --- open rhythmbox music player

---

### Post by forestpixie on 2008-06-14
Bit odd - what have you got for Preferred Apps - multimedia ?

Also have a look in gconf-editor - navigate to apps/rhythmbox/plugins/cd-recorder

mine has 2 keys - active and hidden - both are enabled, without it doesn't start.

If you have another musicplayer installed does it work if you change the options to use that - or does it not work for any music app?

---

### Post by forestpixie on 2008-06-14
If you open the media preferences in Nautilus again - at the bottom is a check box for Never prompt or start on media insertion - is that enabled?

---

### Post by alienexplorers on 2008-06-14
I checked gconf-editor and the items you mentioned are checked.  The preferred multimedia player is rhythmbox. For your second question, yes it is enabled.

Noted something new.  When I was trying to play the music cd I was using my DVD/CD Player drive.  I tried it in my old CDR/CDRW Burner and it worked.  This is strange!!!!

---

### Post by Sef on 2008-06-14
Did you install the [codecs]("https://help.ubuntu.com/community/RestrictedFormats")?

---

### Post by ChameleonDave on 2008-06-14
> **alienexplorers said:**
> Noted something new.  When I was trying to play the music cd I was using my DVD/CD Player drive.  I tried it in my old CDR/CDRW Burner and it worked.  This is strange!!!!

Maybe your DVD drive is malfunctioning.  Can you use other media in it?

Otherwise, there may be some misconfiguration that doesn't let those programs automatically access that drive as an audio CD player.

---

### Post by forestpixie on 2008-06-14
> For your second question, yes it is enabled. 

If that's the answer to > check box for Never prompt or start on media insertion - is that enabled?

then it needs to be disabled :)

---

### Post by alienexplorers on 2008-06-14
Sef, Yes I have all codec's installed

ChameleonDave, Yes the DVD drive works fine with data disk and the ubuntu install disk.

forestpixie, my media menu is setup exactly the same as yours is.

I think it may be a problem with the disk so I am trying to reburn it again as an audio cd to see if it fixes the problem with playing it in the DVD drive.

---

### Post by alienexplorers on 2008-06-14
Took the data disk I used to burn the first audio cd that did not work in the dvd drive and used it again to burn a new audio disk.  This time after it was done burning I put it in the dvd drive and rhythmbox started right up.  Something must have happened to the original audio disk since it worked when I first made it.  Well looks like the problem is solved.  Thanks to everyone for there help.  Next time I will reburn a new disk before getting on here and acting like a dumb ***.

---

### Post by ChameleonDave on 2008-06-14
It's interesting that although the disc was faulty, it did work OK in the CD drive.  Only the DVD drive choked on it.  This implies that the DVD drive is less error-tolerant. 

I have found the same to be the case with mine.  DVD drives seem to slowly get buggier and buggier over their lifetimes.  I've had to get new ones before.

---

### Post by forestpixie on 2008-06-14
> Next time I will reburn a new disk before getting on here and acting like a dumb ***.
Always good to take your daft head out for a drive from time to time :)

for instance - [http://ubuntuforums.org/showthread.php?t=519482](http://ubuntuforums.org/showthread.php?t=519482)

I've had problems before where a new drive spat out a disc constantly - tried a really old drive and it was fine.

---

