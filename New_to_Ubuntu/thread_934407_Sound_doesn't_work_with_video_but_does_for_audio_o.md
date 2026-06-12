---
title: "Sound doesn't work with video but does for audio only files"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by bidness on 2008-09-30
I have install Hardy 8.04 on my HP pavilion laptop and most everything works great.  I just can't get sound when playing video.  I can play mp3s and even rm files, but when trying to play a dvd a get the video just fine, but no audio.  This happens with both Media Player and VLC.  I have been looking around to try to find this problem posted somewhere and have come up with nothing.  I have an nVidia HDA card.  I am hoping to drop windows and just run Linux, but this would be quite the show stopper.  Thanks for any help.

---

### Post by Nxion on 2008-09-30
It sounds like that there is just not the proper codec installed for what you are trying to play.

Follow this: [http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Codecs), as well as the part just below that labeled:

**"Installing DVD Support" **


I had the same problem and after I followed the above, it works fine now, no issues. Let me know if that worked or not or if you need additional help.  Good Luck.

:D

---

### Post by bidness on 2008-10-01
Ok, so I tried the link that you gave and followed all of the instructions then rebooted (just in case) and still a no go.  I have no idea where to go from here.  I have tried Movie Player and MPlayer and VLC.  

Also it appears that I forgot to mention that I am running 64bit version.  Any help would be wonderful.

---

### Post by Nxion on 2008-10-01
Ahhh, now it makes sense. Try this guide. It is for 64-Bit
[URL="http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html"]
http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html[/URL]

Let me know if it worked.

---

### Post by bidness on 2008-10-01
That was almost exactly the same tutorials that were from the other link except that the source.list was different.  I added what was there, but still a no go.  Though I am now getting an error from MPlayer when I type gmplayer into the terminal I get this error message:

```
Too many video packets in the buffer: (4096 in 8265555 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
```

I tried running 
```
gmplayer -ni
```
but still get the error.  I have tried getting all of the updated codecs but still a no-go.  Thanks for sticking with me, I hope that you can help.

---

### Post by Nxion on 2008-10-07
> **bidness said:**
> That was almost exactly the same tutorials that were from the other link except that the source.list was different.  I added what was there, but still a no go.  Though I am now getting an error from MPlayer when I type gmplayer into the terminal I get this error message:

```
Too many video packets in the buffer: (4096 in 8265555 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
```I tried running 
```
gmplayer -ni
```but still get the error.  I have tried getting all of the updated codecs but still a no-go.  Thanks for sticking with me, I hope that you can help.

Let me do a little research on this and I will get back to you.

Nx

---

### Post by Nxion on 2008-10-14
Well I'm sorry but I am stumped about this one. Sorry I could not be of anymore assistance.

---

