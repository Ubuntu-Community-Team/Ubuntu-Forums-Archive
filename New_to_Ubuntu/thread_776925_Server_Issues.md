---
title: "Server Issues?"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by CoeusTitan on 2008-05-01
Hey everyone, I just upgraded from Gutsy to Hardy.

But now, when I try to install packages through Synaptic, I've noticed that I can't download anything, or if I CAN download any files....it goes VERY slowly...around 30 kb/s

Normally, I download at around 1.2 Mb/s

Hopefully the servers are just being slammed from people upgrading like crazy, and the server priority is just being given to them, not people like me who are trying to download single items through Synaptic :-k

Thanks for your thoughts!

:)

---

### Post by TeoBigusGeekus on 2008-05-01
Do you get your normal speed elsewhere, e.g. torrents, ftp servers, etc.?
If so, then it must be just the servers being jammed.

---

### Post by diablo75 on 2008-05-01
System>Administration>Software Sources

In the first tab (Ubuntu Software) click on the button to the right of "Download From:", then click "Other...".  A new box will pop up.  Click on the button that says Select Best Server.  It will ping about 200 different servers, and the one with the fastest will be shown, allowing you to confirm what it thinks would work best for you and your Internet connection.

Hope this helps!

---

### Post by CoeusTitan on 2008-05-01
I am getting normal speeds elsewhere, yes.

---

### Post by CoeusTitan on 2008-05-01
> **diablo75 said:**
> System>Administration>Software Sources

In the first tab (Ubuntu Software) click on the button to the right of "Download From:", then click "Other...".  A new box will pop up.  Click on the button that says Select Best Server.  It will ping about 200 different servers, and the one with the fastest will be shown, allowing you to confirm what it thinks would work best for you and your Internet connection.

Hope this helps!

Hmm! I never knew that!

I'll try it right now.

---

### Post by CoeusTitan on 2008-05-01
Well, it works....but my download speeds are still wildly variable....I can't stand that.

---

### Post by MobiusNZ on 2008-05-01
Remember that hardy was only released a short time ago, so it is in high demand - everyone clicking "update now" in their update manager will be increasing the load on the apt servers you use.

It comes down to the simple open source perogative - if you don't like it, do it yourself. You could set yourself up as a mirror and let people download off you - that way you can get great speeds.

Otherwise, I suggest if things don't speed up in a couple of weeks, you may wish to find a new mirror.

---

### Post by diablo75 on 2008-05-01
> **CoeusTitan said:**
> Well, it works....but my download speeds are still wildly variable....I can't stand that.

Different files are downloaded from different locations.  The servers you're pointing at with the Software Sources applet house *some* updates, but also keep track of third-party Ubuntu partner projects, such as Open Office.  If I understand it correctly, the software sources simply keeps track of updates available in all the different Universe/Multiverse/etc, but doesn't necessarily house *all* of the actual files you download, since some are coming from third party developers own web servers (which can be overwhelmed more easily by comparison).  This is why on some days, it seems that update for Skype just won't download for anything, but a Linux kernel update never seems to have trouble (just an example).

If watching your download speeds vary so greatly bothers you, minimize your update manager and go get a cup of coffee or do something arbitrary to pass the time.

:)

---

### Post by CoeusTitan on 2008-05-01
> **diablo75 said:**
> 

If watching your download speeds vary so greatly bothers you, minimize your update manager and go get a cup of coffee or do something arbitrary to pass the time.

:)

Good idea, I think I'll do just that.

:D

---

