---
title: "Windows Media Player in Firefox?"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by supton on 2008-08-18
Ok, I've been using Ubuntu for oh about 5 minutes after doing the install.  I hooked up to my router directly, and it's surfing the web.  I went to my local ABC news site, and it wants some Windows Media player so I can see the interactive radar map -- but when I follow the link it does not show a Linux driver.

Is there a driver that I ought to use/download?  I'm a Linux newbie, and I wouldn't claim to be much of a Windows expert either.

Thanks.

---

### Post by mike1234 on 2008-08-18
> **supton said:**
> Ok, I've been using Ubuntu for oh about 5 minutes after doing the install.  I hooked up to my router directly, and it's surfing the web.  I went to my local ABC news site, and it wants some Windows Media player so I can see the interactive radar map -- but when I follow the link it does not show a Linux driver.

Is there a driver that I ought to use/download?  I'm a Linux newbie, and I wouldn't claim to be much of a Windows expert either.

Thanks.


Install this package in Synaptic package manager:
ubuntu-restricted-extras

Installing this package will pull in support for MP3 playback and decoding,
support for various other audio formats (gstreamer plugins), Microsoft fonts,
Java runtime environment, Flash plugin, LAME (to create compressed audio files),
and DVD playback.

Flash is probably your main problem, followed by maybe Java. Depends on the website. Also I would suggest installing plugin for Firefox with whichever media player is on your Ubuntu. (Totem by default) The only reason I can think of why this wouldn't work is if it's Microsoft Silverlight. This install will fix all flash and java related problems I know of. 

M.

---

### Post by supton on 2008-08-18
Thanks, will give that a try.

[edit] Did that, restarted Firefox, didn't play.  Will try again tomorrow.

---

### Post by mike1234 on 2008-08-18
> **supton said:**
> Thanks, will give that a try.

[edit] Did that, restarted Firefox, didn't play.  Will try again tomorrow.

Post link for your website and I'll see if it works for me.

M.

---

### Post by eriqjaffe on 2008-08-18
I think you just need the mozilla-mplayer package.

From a terminal:

```
sudo apt-get install mozilla-mplayer
```, or you can install it through the Synaptic Package Manager (they both, essentially, do the same thing).

---

### Post by pjones0404 on 2008-08-18
i have followed the steps in this post and have never had an issue with things not playing correctly. i have used it on various machines and it works like a charm. check it out and see if after running all the commands listed if the file will play. 

[http://ubuntuforums.org/showthread.php?t=766683&highlight=media+comprehensive](http://ubuntuforums.org/showthread.php?t=766683&highlight=media+comprehensive)

---

### Post by supton on 2008-08-19
> **pjones0404 said:**
> i have followed the steps in this post and have never had an issue with things not playing correctly. i have used it on various machines and it works like a charm. check it out and see if after running all the commands listed if the file will play. 

[http://ubuntuforums.org/showthread.php?t=766683&highlight=media+comprehensive](http://ubuntuforums.org/showthread.php?t=766683&highlight=media+comprehensive)

Thank you for the link; I did steps 1 and 2, and did a reboot also, but it still does not work.  I'll retrace my steps and reread the troubleshooting section.

The website is:
[www.wmur.com](www.wmur.com)
in particular:
[Radar Map]("http://www.wmur.com/weather/grid.html#HEARSTWX=http%3A//www.wmur.com/weather/15643496/liveradar.html%3Fqs%3D%3Blongname%3DLive%2520Radar%3Bshortname%3DLive%2520Radar")

---

### Post by Orlsend on 2008-08-19
To tell you the truth I used to have this problems, I can access the web-site and watch videos there... I wish i coul tell you what I did...I just searched Codec in "Add/remove" and installed every single one except "Gnash" (That evil piece of Malware)

---

### Post by philinux on 2008-08-19
[http://www.wmur.com/weather/grid.html#HEARSTWX=http%3A//www.wmur.com/weather/15643496/liveradar.html%3Fqs%3D%3Blongname%3DLive%2520Radar%3Bshortname%3DLive%2520Radar](http://www.wmur.com/weather/grid.html#HEARSTWX=http%3A//www.wmur.com/weather/15643496/liveradar.html%3Fqs%3D%3Blongname%3DLive%2520Radar%3Bshortname%3DLive%2520Radar)

Viewing this page gives a white rectangle where the flash should be and causes flash to crash for me. I have to close and re-open firefox.

---

### Post by Nepherte on 2008-08-19
I get the same white rectangular box, it doesn't crash though.

---

### Post by philinux on 2008-08-19
> **Nepherte said:**
> I get the same white rectangular box, it doesn't crash though.

What I meant was flash no longer works after visiting that site.
Closing and re-starting FF enables flash again.

---

### Post by linuxguymarshall on 2008-08-19
I recommend installing the flash player and if you want windows media player try using a firefox plugin to make the site think you are using internet explorer and install it.

---

