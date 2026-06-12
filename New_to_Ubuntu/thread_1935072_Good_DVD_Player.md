---
title: "Good DVD Player"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by Sunfist on 2012-03-03
I am looking to install a good dvd player for Ubuntu. The one it comes with tells me it needs an add-on to play my dvd and then when I tell it to search for one, it comes back and says it can't find one...so I don't know. Just wondering if anyone has found one they really like.

---

### Post by mike555 on 2012-03-03
If you are trying to play an dvd that you bought , it probably is drm'ed  , so you need to go to [http://medibuntu.org/](http://medibuntu.org/) and read about how to get the decoder.

---

### Post by Daveth on 2012-03-03
and when yu have done that, fire up vlc to play it.

---

### Post by nd456 on 2012-03-03
I don't mean to question Ubuntu experts... but can't VLC play encoded dvd's out of the box?

---

### Post by _0R10N on 2012-03-03
@nd456

Yes, it can. VLC rules.

---

### Post by sammiev on 2012-03-03
Likes VLC myself.

---

### Post by Aclaybor on 2012-03-03
It should most certainly play DVD's after install. If not, and I have had this happen before, it doesn't play them, you could always search for an encoder.

---

### Post by souravc83 on 2012-03-04
I've never tried playing a DVD with Ubuntu.
However, in general for playing different kinds of media, I've found the mplayer very powerful.
Mplayer might be useful for you. If you do not like the fully command line version, you can use a GUI frontend. I use the Gnome-mplayer sometimes, when I do not do command line.

---

### Post by wildmanne39 on 2012-03-04
Hi, +1 for VLC I use it myself for dvd play back.

---

### Post by Sunfist on 2012-03-04
Well I installed VLC and it doesn't work either. I guess that's why people prefer windows over linux. I can run media player under win7 and it plays the dvd just fine, first time, no problem, no extras to add, it just works. Linux...different story.

---

### Post by uRock on 2012-03-04
> **Sunfist said:**
> Well I installed VLC and it doesn't work either. I guess that's why people prefer windows over linux. I can run media player under win7 and it plays the dvd just fine, first time, no problem, no extras to add, it just works. Linux...different story.

You agreed to a EULA in Windows which allows the DVD to be played. To install the needed packages for playing DVDs enter the following two commands into a terminal,

32bit```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb

sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```64bit```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
```
As for VLC, I do not recommend it.

---

### Post by Sunfist on 2012-03-05
Thanks uRock, I now have VLC working perfectly. The movie player that comes with ubuntu still doesn't work, but that's okay. VLC works and the quality of playback is absolutely first rate.:D

---

### Post by deusabscondus on 2013-04-14
i can't get VLC to play a commercial video (plays dloaded vids fine) When I try a commercial video it seems to know it is there, but won't play and then invariably hangs on me, forcing me to remove dvd from drive as only way to shut VLC down

What player can you recommend.
thx

---

### Post by howefield on 2013-04-14
Best to start a fresh thread.

Old thread closed.

---

### Post by wildmanne39 on 2013-04-14
Thread closed. Please do not post in old threads.

---

