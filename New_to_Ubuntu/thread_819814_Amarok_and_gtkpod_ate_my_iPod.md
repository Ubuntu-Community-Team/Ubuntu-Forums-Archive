---
title: "Amarok and gtkpod ate my iPod"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by ProPyro on 2008-06-05
Ok, this is a problem I've been dredging myself through for a few weeks now.  Awhile ago I asked what program would be best for managing music on an iPod and several people suggested Amarok.  It seemed like it was working until I tried to add music to the player, then it just lost everything.  The iPod says that it doesn't have any music on it, but it also says that it only has X number of gigs left on the device.  So it knows something is there, but it won't register it as music.

So I looked up a guide that seemed helpful, [this]("http://www.linuxjournal.com/article/9266") one to be specific, and decided to try out gtkpod.  It seems like a pretty good program and looks easy enough to use.  Instead of just trying to add more music to my iPod this time though, I used gtkpod to delete all the music on it and tried to add my entire collection back onto it.  Well that got me the same result.

I read somewhere that I might have to delete the content of my iTunes folder, but I can't remember where I saw that and don't want to try that because I don't have access to windows anymore to try to fix what I've done.  Do any of you have any idea how to fix my problem?  I'd appreciate any help you can give, thanks.

---

### Post by kostkon on 2008-06-06
> **ProPyro said:**
> Ok, this is a problem I've been dredging myself through for a few weeks now.  Awhile ago I asked what program would be best for managing music on an iPod and several people suggested Amarok.  It seemed like it was working until I tried to add music to the player, then it just lost everything.  The iPod says that it doesn't have any music on it, but it also says that it only has X number of gigs left on the device.  So it knows something is there, but it won't register it as music.
Sorry to hear that.

You could have also used *Rhythmbox*, which comes with *Ubuntu*.
> **ProPyro said:**
> So I looked up a guide that seemed helpful, [this]("http://www.linuxjournal.com/article/9266") one to be specific, and decided to try out gtkpod.  It seems like a pretty good program and looks easy enough to use.  Instead of just trying to add more music to my iPod this time though, I used gtkpod to delete all the music on it and tried to add my entire collection back onto it.  Well that got me the same result.
Indeed, *gtkpod* is a good program but with a strange GUI. 

Nevertheless, from my experience *gtkpod* does checksums and in most cases repairs the *iTunesDB* file (the file that holds your iTunes database, i.e. your songs list) automatically.

If you had added some songs, instead of deleting everything, there is a possibility that *gtkpod* would had repaired the library.
> **ProPyro said:**
> I read somewhere that I might have to delete the content of my iTunes folder, but I can't remember where I saw that and don't want to try that because I don't have access to windows anymore to try to fix what I've done.  Do any of you have any idea how to fix my problem?  I'd appreciate any help you can give, thanks.
The problem is that for some reason your *iTunesDB* file got corrupted.

You can try to use [*Floola*]("http://www.floola.com/"), it is a very good iPod management application, although it's closed source, if you care to know. 

*Floola* gives you an option to repair your database so this may solve your problem.

What *iPod* do you have?

---

### Post by ProPyro on 2008-06-06
> **kostkon said:**
> What *iPod* do you have?
A 160 gig classic, which should be the current generation.

---

