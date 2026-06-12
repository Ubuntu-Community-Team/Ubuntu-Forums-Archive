---
title: "no youtube video"
date: 2013-05-23
forum: New to Ubuntu
---

### Post by adamAL370 on 2013-05-23
Hi all,
Absolute newbie here.Just upgraded to 12.04 from 10.04.on a Toshiba Tecra8100. S3 Savage video/850mhz cpu. Youtube pages will load but just black screen and no video playing. No sound either. ShockWave Flash v11.2 is enabled. The youtube video wasn't play on 10.04 either.Please help. Thanks.

---

### Post by papibe on 2013-05-23
Hi adamAL370. Welcome to the forums ):P

Close your browser, open a terminal and run these commands:
```
sudo apt-get update

sudo apt-get updrade

sudo apt-get install ubuntu-restricted-extras
```
The, open Firefox and check youtube videos.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by kostkon on 2013-05-23
Latest versions of Flash require a CPU that supports the SSE2 instruction set; your Pentium 3 CPU only supports up to SSE.

---

### Post by newb85 on 2013-05-23
From what I've read, Chrome's Pepper Flash doesn't work with SSE, either.

---

### Post by papibe on 2013-05-23
An alternative would be to subscribe to youtube's [html5 trial]("http://www.youtube.com/html5").

You would be able to play lot of youtube videos (not all though).

Regards.

---

### Post by adamAL370 on 2013-05-23
Hi,
Did the sudo things, no luck. Still the black screen. Yeah,I thought about the cpu,the thing is for four or five years I had XP on this machine the video was always working.Hmm...the other alternative is to reverse back to XP,reluctantly.

---

### Post by newb85 on 2013-05-23
I may be missing something, but I don't think switching back to Windows will fix the problem.  The problem is independent of your OS.  Yes, it *used to* work in XP, with what was at that time the latest version of Flash (which didn't require SSE2).  At that time, your CPU would support the latest Flash in Ubuntu, too.  The problem is your CPU won't support a version of Flash new enough for YouTube.

Again, I may be missing something.

---

### Post by monkeybrain2012 on 2013-05-23
Install gecko-mediaplayer from the repo, then install the greasemonkey addon for Firefox, then install this greasemonkey script [http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)

You don't need flash for Youtube.

---

### Post by adamAL370 on 2013-05-23
Thanks for the head up. I'll look into this option.I might need a hand on the installtion procedures,later.

---

### Post by s1baker on 2013-05-24
You may need to go to Adobe's repository and try an earlier version of libflashplayer.so
( libflashplayer.so is in  /usr/lib/flashplugin-installer )

I had to go back to version 10 something to get my 8 year old 32 bit computer
to play youtube videos.

---

### Post by adamAL370 on 2013-05-25
Good news.I installed the ViewTube and it worked.Now the Youtube video is playing.Thanks for all the helps particularly MonkeyBrian.I might also look into Adobe's older version players later.Thanks again.

---

