---
title: "[SOLVED] Totem Movie Player codexes"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by thadacto on 2008-11-27
While waiting for a reply to my first question, I thought I might watch a video.
However, Totem doesn't seem to support mpg files, avi files nor adobe flash flv files. 
Where do I get these supporting files from????

Is it really worth trying to use linux with all this hassle?

---

### Post by taurus on 2008-11-27
You probably need the ubuntu-restricted-extras package.

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Keen101 on 2008-11-27
> **thadacto said:**
> 
Where do I get these supporting files from????

just search for "gstreamer" or "avi" in Add/Remove (make sure you select "all available software") or in synaptic.



> **thadacto said:**
> Is it really worth trying to use linux with all this hassle?

it's really not that much of a hassle. once it's done, you shouldn't have a problem.

---

### Post by Olivier2371 on 2008-11-27
Hello and Welcome,

You need the following codec from ADD/Remove under Applications.

GStreamer ffmpeg video plugin.

But normally ToTEM ask you if you want to search for the codec.

Hope this helps.

Keen101,taurus,

Sorry Guys didn't realize you posted.

---

### Post by thadacto on 2008-11-28
Here we go - a new day. Up msot of the night upgrading so that I can move on to version 7.10 and then upwards to 8.04.

I appear to have all the codexes installed because the install/remove won't let me remove them.
ALSO I have now got KMPlayer working and can view AVI and mpg files though I could use something for flash flv files. As I understand it, macromedia doesn't support AMD 64. Am I correct?

Furthermore, I can't remove Totem as it appears to have something to do with the whole system. Correct??

---

### Post by bhadotia on 2008-11-28
> **thadacto said:**
> Here we go - a new day. Up msot of the night upgrading so that I can move on to version 7.10 and then upwards to 8.04.

I appear to have all the codexes installed because the install/remove won't let me remove them.
ALSO I have now got KMPlayer working and can view AVI and mpg files though I could use something for flash flv files. As I understand it, macromedia doesn't support AMD 64. Am I correct?

Furthermore, I can't remove Totem as it appears to have something to do with the whole system. Correct??

Try vlc. That will play .flv:
```
sudo apt-get install vlc
```
Don't remove totem untill you upgrade to intrepid as it is dependency for the package ubuntu-desktop in the earlier versions of ubuntu. You need ubuntu-desktop package to ensure proper upgrade of the system. There is a link in my signature which will address all your multimedia related issues. It would be worthwhile if you take the time to go through [that]("http://ubuntuforums.org/showthread.php?t=766683").

---

### Post by menschtx on 2009-01-08
I added the suggested codecs and am still getting an error about not being able find the location. The file is on the desktop, when trying to open the file from the desktop, the player closes.

---

### Post by meka4996 on 2009-05-23
Try this one...
[http://ubuntuforums.org/showthread.php?t=1103825](http://ubuntuforums.org/showthread.php?t=1103825)

---

