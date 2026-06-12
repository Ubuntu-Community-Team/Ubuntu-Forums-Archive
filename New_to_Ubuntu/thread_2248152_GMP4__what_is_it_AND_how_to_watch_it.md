---
title: "GMP4  what is it AND how to watch it"
date: 2014-10-12
forum: New to Ubuntu
---

### Post by briar rabbit on 2014-10-12
Hi everyone,

I just got a CD-R from the police that I want to use as evidence against them in court.  The problem is I can not open/play the CD-R.  I can play other CD-R's but not this one.  Movie Player - NOPE.  VLC - NOPE.  Even the neighbors other OS - WONT DO IT! Hmmm.  So I found out that the CD-R is an Avi it is also a GMP4 which is a DIGITAL CCTV (and only two other people know what all else). 

Any old hoot. I searched the internet and found mostly people trying to sell me unrelated but excellent thingies that I'm sure I will be buying soon but, in the now time ... GMP4 does not seem to make very many search returns - oh yeah this one for sure; ubuntuforums.org/showthread.php?t=1604680 

So, can some kind old soul tell me; is GMP4 so common it is not mentioned or is it so un-common that it is not mentioned?  Or, ?

---

### Post by grahammechanical on 2014-10-12
> [COLOR=#333333][FONT=Lucida Grande]GMP4 appears to be GeoVision Advanced MPEG-4 Video Codec, a proprietary codec used by video surveillance cameras. And it's not supported by VLC.[/FONT][/COLOR]

[https://forum.videolan.org/viewtopic.php?f=2&t=84872](https://forum.videolan.org/viewtopic.php?f=2&t=84872)

Note: It is proprietary. 

[http://www.experts-exchange.com/Software/MultiMedia_Applications/Q_26989588.html](http://www.experts-exchange.com/Software/MultiMedia_Applications/Q_26989588.html)

You want Mplayer. This is a long list but just about half way down you will see GeoVision Advanced MPEG-4 and it includes GMP4

[http://www.mplayerhq.hu/DOCS/codecs-status.html](http://www.mplayerhq.hu/DOCS/codecs-status.html)

Regards.

---

### Post by briar rabbit on 2014-10-13
Thanks for the reply  grahammechanical but, I am still having problems.

The link - [https://forum.videolan.org/viewtopic.php?f=2&t=84872](https://forum.videolan.org/viewtopic.php?f=2&t=84872) - sent me to "Instructions for installing GMP4 Codec:
ftp://geo-demo-japan.dipmap.com/FAQ/GV-System/Fail_to_play_back_video-v-a.pdf"

It says to install "GeoCodecReg.exe".

===

I do not understand; "You want Mplayer. This is a long list but just about half way down you will see GeoVision Advanced MPEG-4 and it includes GMP4

http://www.mplayerhq.hu/DOCS/codecs-status.html"

I already have mplayer.  The driver at this site is "GXAMP4.dll". 

I searched for this in synaptic package manager it is not there.


Do you know if these files themselves can be converted to something more conventional?

======[URL="http://www.mplayerhq.hu/DOCS/codecs-status.html"]

 [/URL]I found this;
[http://rpmfind.net/linux/RPM/sourceforge/p/po/postinstaller/fedora/releases/19/x86_64/updates/w32codecs-1.0-20110131.fc19.x86_64.html](http://rpmfind.net/linux/RPM/sourceforge/p/po/postinstaller/fedora/releases/19/x86_64/updates/w32codecs-1.0-20110131.fc19.x86_64.html)

Would it be safe and would it allow me to watch gmp4's?

---

### Post by stalkingwolf on 2014-10-13
you might try handbrake to convert them.  I use it to get rid of shadow boxing.

---

### Post by briar rabbit on 2014-10-15
thanks grahammechanical and stalkingwolf

I have found out that the thing is completely proprietary.

The only available codec are made for another operating system.

I am particular about this - I AM ANGRY! Damn it.

OK I apologize for my outburst.

I did not ask for this thing so I will do my best to let them know when they get it back just exactly who has returned it to sender.

Cheers

---

### Post by mc4man on 2014-10-15
Try here - 
[http://ubuntuforums.org/showthread.php?t=2149564](http://ubuntuforums.org/showthread.php?t=2149564)
> /all-20110131$ ls | grep GXAMP4
GXAMP4.dll
Note that these codecs are only for mplayer on a 32bit install

---

### Post by briar rabbit on 2014-10-15
Hello mc4mn

I just looked at the link, 6 pages. I did a search from the find function for "GXAMP4" and another for "GMP4" to see where the relevant parts were and it is nowhere on the pages.?
So what else am I suppose to look for?

---

### Post by mc4man on 2014-10-15
> **briar rabbit said:**
> Hello mc4mn

I just looked at the link, 6 pages. I did a search from the find function for "GXAMP4" and another for "GMP4" to see where the relevant parts were and it is nowhere on the pages.?
So what else am I suppose to look for?

It's a How to build mplayer & part of the howto, ie. Post 1,  shows how to download & install the w32codecs of which GXAMP4.dll is one.
Then **if on a 32 bit install **try playing in mplayer. 
If that doesn't work then follow the complete howto & build your own recent mplayer & try again.

If you're on a 64 bit install then don't bother, can't work.

(- look at this section
Codecs...

MPlayer benefits from the use of some external codecs and these can be downloaded directly from the MPlayer website. The following is a single command:
.........

---

### Post by andrew.46 on 2014-10-16
As mc4man has mentioned only 32bit MPlayer with the extra codecs will play this under Linux:

```

andrew@ilium~$ **[COLOR="#FF0000"]mplayer -vc help | grep -i GXAMP4[/COLOR]**
geomp4      vfw       working   GeoVision Advanced MPEG-4  [GXAMP4.dll]

```

Looks like the company Geovision not only sells the video cameras but also the software to save and manipulate the video, thus their interest in having a proprietary codec. But all is not lost as long as you have a *32bit *installation of MPlayer, then you can play the files with a nice gui like SMPlayer.

**Edit:** I have[ added a note]("http://ubuntuforums.org/showthread.php?t=2149564&p=13145314&viewfull=1#post13145314") regarding this codec...

---

