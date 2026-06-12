---
title: "Firefox Lockup"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by boltz101 on 2008-09-04
Hi guys,

Just wonder if anyone can help at all.

I made a recent install of Ubuntu and I really like using it.  Unfortunately, when I go into Firefox it pretty much hangs after about 1-2 mins and I have to switch my machine on and off again.

Any help appreciated, complete Linux and kernal n00b so if it gets too technical I will have to give up!

Thanks.

---

### Post by baruch60610 on 2008-09-04
I've had problems with Firefox, though not quite as fast as yours (I usually lock up after a few hours).

First, what version of FF are you using?  I seem to have more problems with 3 than I had with 2.

What sorts of changes, if any, did you make to Firefox?  I mean, did you add a bunch of add-ons, anything like that?

When Firefox locks up, that usually means it's hogging a lot of the computer's CPU time, which means everything runs very slowly - so slow, you think nothing's moving.  Usually it *is* moving, if you give it enough time.

When you restart your computer and start FF again, do you get a message saying something like "Firefox ended unexpectedly.  Do you want to restart the session or begin a new session?" (something like that, anyway).  If you do, then choose to start a *new* session, not restart the old one.  Sometimes the problem is some Web page Firefox doesn't handle well, and if you keep trying to get to it (restarting the frozen session), you'll keep on freezing.

If all of this doesn't work, then maybe you could remove Firefox and reinstall it, using the "add/remove" programs menu option.  I don't like to suggest that, but sometimes it clears a problem that otherwise won't go away.

---

### Post by boltz101 on 2008-09-04
> **baruch60610 said:**
> 

If all of this doesn't work, then maybe you could remove Firefox and reinstall it, using the "add/remove" programs menu option.  I don't like to suggest that, but sometimes it clears a problem that otherwise won't go away.


Read through your whole post and was going to reply individually then decided that this very simple thing might be the best.

I have put a few addons in, but nothing that I know doesnt work on friends machines with Ubuntu (or other flavours) installed.

---

### Post by philinux on 2008-09-04
To see if addons are the problem, run FF in safe mode.

Open a terminal and use

```
firefox -safe-mode
```

---

### Post by hh holmes on 2012-09-04
Safe mode worked for me.  Thanks Philinux.  That was getting obnoxious, even after a reinstall Firefox was still attempting to restore a prior crash.

---

