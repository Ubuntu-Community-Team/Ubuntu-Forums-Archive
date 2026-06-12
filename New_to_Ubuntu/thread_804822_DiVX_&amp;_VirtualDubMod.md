---
title: "DiVX &amp; VirtualDubMod"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by H.Callahan on 2008-05-23
I am hoping that a new computer (more capable of doing video stuff) is in the wings and I would like to know:

1. Is there an equivalent program to the VirtualDubMod that runs on Windows?  I have tried to install it under Wine, and it kinda runs ok, but after trying to install DiVX Pro in Wine, which seems to install ok, VDub does not see the codec.  Winehq does not have much info on VDub.

2. Assuming that there there is a (1), is DiVX (not Xvid) available for Ubuntu?

The ultimate goal is to get DiVX Home Theater Certified files created completely without Windows.  

BTW, before anyone asks, the reason for this is that I have a DiVX Home Theater Certified stand-alone DVD player.  It will play Xvid files, but without basic features like fast forward and reverse.  Therefore the Xvid codec is not a completely acceptable solution.

---

### Post by shifty_powers on 2008-05-23
gordian knot?

no longer in development, afaik, but then it doesn't need to be, it works ;)

[http://sourceforge.net/projects/gordianknot](http://sourceforge.net/projects/gordianknot)

---

### Post by TenPlus1 on 2008-05-23
Avidemux is in the repo's and does a great job of manipulating and converting movies...

---

### Post by H.Callahan on 2008-05-23
Isn't GK Windows only or am I missing something?

I'll take a look at Avidemux.

---

### Post by disturbedite on 2008-05-23
yes, definitely avidemux is VD's linux equivalent.  no, actually, avidemux is much better than VD!

---

### Post by H.Callahan on 2008-05-23
I just installed avidemux and it initially seems reasonable.  The next question is can real, 100% genuine, DiVX be used on Ubuntu for coding?

---

### Post by SunnyRabbiera on 2008-05-23
> **H.Callahan said:**
> I just installed avidemux and it initially seems reasonable.  The next question is can real, 100% genuine, DiVX be used on Ubuntu for coding?

xvid is probably your best bet as divx is closed source, ubuntu mainly uses free software alternatives when available.
But I think that most of the xvid codecs and stuff should work for you.

---

### Post by H.Callahan on 2008-05-23
My problem with Xvid is that, on my DVD player, files encoded with it do not respond to fast forward or reverse (they will pause, though) and will not allow jumping to a specific time within the video.  Actual DiVX files will.

Assuming DiVX can't be had for Ubuntu, does anyone know anything about running DiVX under Wine to use with VirtualDubMod?

---

### Post by shifty_powers on 2008-05-23
not looking good on that one....

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7829](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7829)

---

### Post by shifty_powers on 2008-05-23
heh no results for divx pro codec...

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2492](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2492)

---

### Post by SunnyRabbiera on 2008-05-23
well before doing anything drastic, try installing the ubuntu-restricted-extras package along with the gstreamer plugins, good, bad, ugly.
also try medibuntu too, there might be something for you in the repositories as well if you know how to use them.

---

### Post by H.Callahan on 2008-05-23
Carp.

I will look around some more, but this will probably force me back to a dual boot situation again.

---

### Post by SunnyRabbiera on 2008-05-23
> **H.Callahan said:**
> Carp.

I will look around some more, but this will probably force me back to a dual boot situation again.

I dont think this will be the case, by all accounts I do think its possible to get Divx videos working in linux, I just never dont it as I dont use divx.
I can give you lessons on how to use the repositories if you need me to

---

### Post by H.Callahan on 2008-05-23
Oh, I can get DiVX files to play in Ubuntu.  That is not the problem.  The problem is that I have a tabletop DVD player hooked to my TV.  This tabletop player is capable of playing native DiVX encoded files that have been burnt to a CD or DVD.  The player will not play Xvid encoded files with all the features -- like fast forward, reverse and time jumping -- available.

Therefore I need a way to recompress any videos, even Xvid, with real, genuine, honest-to-god DiVX so that I can burn them to CD/DVD and have them play, full-featured, in the desktop box.

---

### Post by fiddledd on 2008-05-23
Here might be what you need: [http://labs.divx.com/DivXLinuxCodec](http://labs.divx.com/DivXLinuxCodec)

It seems like it's Divx Pro but for Linux. Sorry if I've misread it, I'm rushing abit before I go offline:)

---

### Post by H.Callahan on 2008-05-23
I'll give that a try.  It looks complicated and I don't know how hopeful to be given the comments, but at least it's something!

Thanks!

---

### Post by disturbedite on 2008-05-24
just get a KISS player, they support practically every audio & video format under the sun...

---

### Post by H.Callahan on 2008-05-27
> **fiddledd said:**
> Here might be what you need: [http://labs.divx.com/DivXLinuxCodec](http://labs.divx.com/DivXLinuxCodec)

It seems like it's Divx Pro but for Linux. Sorry if I've misread it, I'm rushing abit before I go offline:)

Well, it appears that is some sort of API, probably good for coding DiVX into an application.  I can't tell whether the actual codec has been installed or not.  It (DiVX) does not appear in the list of Avidemux as usable codec.  Where do codecs generally get installed in Ubuntu?

---

### Post by H.Callahan on 2008-05-27
> **disturbedite said:**
> just get a KISS player, they support practically every audio & video format under the sun...

I'd love to!  Please feel free to mail me donations towards getting one!

:-D:-D

---

