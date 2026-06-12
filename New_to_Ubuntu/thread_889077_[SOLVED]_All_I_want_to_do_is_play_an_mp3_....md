---
title: "[SOLVED] All I want to do is play an mp3 ..."
date: 2008-08-13
forum: New to Ubuntu
---

### Post by jfbays on 2008-08-13
I downloaded a couple of mp3s (they downloaded to the desktop, which was, a bit, unexpected); I clicked on one of them (expecting it to play); the Totem Movie Player opened (WTF?); nothing happened.  I tried to "Open With" Rythembox; still nothing happened...

How can I play a simple mp3 using Ubuntu and what is offered with Ubuntu?  

While I'm waiting for an answer, I'm going to download the mp3s with my Windows machine, burn them, and enjoy listening to them...It just works...

---

### Post by dje on 2008-08-13
ubuntu does not come with the mp3 codecs because they are proprietary and non free. follow the guide [here]("http://www.ubuntu1501.com/2008/04/easy-media-codec-installation-for-hardy.html") to install them ;)

dje

---

### Post by OutOfReach on 2008-08-13
Type this into the terminal (Applications>Accessories>Terminal):
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by jfbays on 2008-08-13
Thanks guys.  I'll say more later...

---

### Post by starcannon on 2008-08-13
While your at it you might as well have your cake, blow out the candles, and eat it to; that said, be sure to grab this stuff as well:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

That repository will help you get the rest of your codecs installed.

---

### Post by jfbays on 2008-08-13
Things are working. Thanks everybody. For what it's worth, I like Ubuntu, and the Ubuntu philosophy, but the transition is sometimes frustrating...

Thanks again,
jfbays

---

### Post by halitech on 2008-08-13
as to the downloading to your desktop, if you downloaded them with firefox, go to edit - preferences and on the main tab, change the default download location to a place of your choosing (inside your home folder of course)

---

### Post by Darkade on 2008-08-13
This is an excellent guide for MP3 and other restricted formats
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by jfbays on 2008-08-14
I ran this:
```
sudo apt-get install ubuntu-restricted-extras
```
a bunch of stuff was installed.  Where can I find a list of what was actually installed?

I have been reading the other information offered as well, thanks everyone...

---

### Post by LowSky on 2008-08-14
> **jfbays said:**
> I'm going to download the mp3s with my Windows machine, burn them, and enjoy listening to them...It just works...

Windows doesn't just work. You need codecs for OS too. Your just used to it.

---

### Post by jfbays on 2008-08-14
You are correct, my friend.  It's easy to forget that it took years (3 service packs + countless updates) to get my XP machines to a point where I can use them efficiently.  And now MS is talking about dropping XP support.  These days, however, I'm spending most of my time on my new Ubuntu machine, and learning more and more by the hour.  I think Ubuntu, and all that it has to offer, is my future...

---

