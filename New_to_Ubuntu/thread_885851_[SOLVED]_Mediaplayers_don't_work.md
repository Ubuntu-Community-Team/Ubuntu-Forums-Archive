---
title: "[SOLVED] Mediaplayers don't work"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by speedzor on 2008-08-10
hi,

when I'm trying to play some songs, the counter of Totem & Rhytmbox doesn't change his position. it keeps standing at second 0.
So no songs are played.

I'm using ubuntu with gnome.
the directory with the songs in it are on a external hard drive.

---

### Post by T2manner on 2008-08-10
do you have permission to use the files?

---

### Post by SunnyRabbiera on 2008-08-10
also got all your codecs installed?

---

### Post by speedzor on 2008-08-10
twice yes.
An hour ago I was still playing them on exactly the same way as I want to do now...

---

### Post by T2manner on 2008-08-10
I don't know what it could be then.
Try restarting your computer.

---

### Post by northern lights on 2008-08-10
Navigate to "System > Administration > Software Sources". Under the first three tabs (Ubuntu Software, Third-Party Software, and Updates) enable all repositories but 'proposed' and 'backports'. Leave "Automatic Updates" untouched also.

From "Applications > Accessories > Terminal" open a shell prompt and run```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get autoremove totem-mozilla && sudo apt-get install libdvdcss2 w32codecs mozilla-mplayer ubuntu-restricted-extras flashplugin-nonfree
```

Codec wise, you'd be now sorted for mp3, wma/wmv, and encrypted DVD playback as well as flash and video web content.

---

### Post by diwas on 2008-08-10
Yes, restart it first.

---

### Post by HullDown on 2008-08-10
You said the directory is on an external hard drive.  Is the drive mounted?  Can you see the song lists?

---

### Post by northern lights on 2008-08-10
> **speedzor said:**
> twice yes.
An hour ago I was still playing them on exactly the same way as I want to do now...Redundant post of mine, then.

...late...

--> Any other sound?

---

### Post by speedzor on 2008-08-10
I've already tried a restart, and it didn't change anything.
And yes, the drive is mounted, I can go trough the different directorys.
Even after updating my codecs, it still can't be played.

edit: I've got some sounds I think, those you get at a startup.
But I'm not completely sure.

---

### Post by SunnyRabbiera on 2008-08-10
> **speedzor said:**
> I've already tried a restart, and it didn't change anything.
And yes, the drive is mounted, I can go trough the different directorys.
Even after updating my codecs, it still can't be played.

edit: I've got some sounds I think, those you get at a startup.
But I'm not completely sure.

It could possibly be the audio driver, if you have not edited it maybe pulseaudio is your issue as I think thats the default now.
Go up to system > preferences > sound.
If all are set on autodetect try changing them to ALSA.

---

### Post by speedzor on 2008-08-10
hehe, thanks!

I've already had this problem once before I reinstalled ubuntu, but I couldn't remember how I solved it.
And yes, you're right, it was also on autodetect.

thanks for helping me out, this one is solved.

---

