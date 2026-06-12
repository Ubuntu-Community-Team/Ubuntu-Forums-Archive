---
title: "[SOLVED] terminal when I turn on - how can I get to normal desktop?"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by lila on 2008-08-10
Hello, 
We've got two computers, one running on Gutsy (this one) and one on Breezy.  The Breezy one since today only comes up with a full screen terminal when we switch  it on, asking us to log in (which we can). But when we do things like cd desktop it tells us that there is no such file or directory. We tried all sorts of things, none of them seem to exist...

We did try to uninstall and reinstall firefox yesterday, because that had problems.  Could that be at the root of it?
There is no seriously important data on the computer, at least none that isn't backed up somewhere else, so would the easiest be to just reinstall everything or is there an easy fix ?
Thanks for any help!
Lila

---

### Post by SunnyRabbiera on 2008-08-10
> **lila said:**
> Hello, 
We've got two computers, one running on Gutsy (this one) and one on Breezy.  The Breezy one since today only comes up with a full screen terminal when we switch  it on, asking us to log in (which we can). But when we do things like cd desktop it tells us that there is no such file or directory. We tried all sorts of things, none of them seem to exist...

We did try to uninstall and reinstall firefox yesterday, because that had problems.  Could that be at the root of it?
There is no seriously important data on the computer, at least none that isn't backed up somewhere else, so would the easiest be to just reinstall everything or is there an easy fix ?
Thanks for any help!
Lila

Breezy is ancient anyway and no longer supported.

---

### Post by T2manner on 2008-08-10
Since there's nothing important on it, just do a fresh install of Hardy Heron.

---

### Post by bpowell2005 on 2008-08-10
> **lila said:**
> Hello, 
We've got two computers, one running on Gutsy (this one) and one on Breezy.  The Breezy one since today only comes up with a full screen terminal when we switch  it on, asking us to log in (which we can). But when we do things like cd desktop it tells us that there is no such file or directory. We tried all sorts of things, none of them seem to exist...

We did try to uninstall and reinstall firefox yesterday, because that had problems.  Could that be at the root of it?
There is no seriously important data on the computer, at least none that isn't backed up somewhere else, so would the easiest be to just reinstall everything or is there an easy fix ?
Thanks for any help!
Lila

I've been hearing that Firefox and Ubuntu are co-dependent...so yes, I'd guess your removing of Firefox led to a problem with the Ubuntu GUI. If you're missing the desktop directory, then it sounds like the GUI might be gone completely. You could try "sudo apt-get install ubuntu-desktop" and it should reinstall the Gnome desktop.

---

### Post by bpowell2005 on 2008-08-10
> **T2manner said:**
> Since there's nothing important on it, just do a fresh install of Hardy Heron.

Yeah, I'd have to agree...although I always like the challenge of trying to fix anything on my installation, I have run into spots where I just need to start over...since this computer isn't critical, a fresh installation may be just what the doctor ordered.

---

### Post by lila on 2008-08-10
> **T2manner said:**
> Since there's nothing important on it, just do a fresh install of Hardy Heron.

... That's all very well, but already with Gutsy we had the problem that it slowed down this computer enormously, we had to buy extra memory.  It had Breezy before which was working fine.  Since the other one is even older (vintage 1998), we don't really want to try Hardy.  
We are considering XUBUNTU or dsl (damn small linux).  The dsl has the slight edge at the moment, because it also recognises *everything* in our 1998 laptop, which no other linux distro we've tried has ever done...
But for the moment, we might just reinstall Breezy because we're used to it.

So, no fixes, I suppose?
Lila

---

### Post by bpowell2005 on 2008-08-10
> **lila said:**
> ... That's all very well, but already with Gutsy we had the problem that it slowed down this computer enormously, we had to buy extra memory.  It had Breezy before which was working fine.  Since the other one is even older (vintage 1998), we don't really want to try Hardy.  
We are considering XUBUNTU or dsl (damn small linux).  The dsl has the slight edge at the moment, because it also recognises *everything* in our 1998 laptop, which no other linux distro we've tried has ever done...
But for the moment, we might just reinstall Breezy because we're used to it.

So, no fixes, I suppose?
Lila

Try "sudo apt-get install ubuntu-desktop"

---

### Post by T2manner on 2008-08-10
I would definitely go with Xubuntu if you're having problems with the newer Ubuntu versions being slow.
It runs good on old computers like yours.

If not, I would just reinstall Breezy to fix the problem.

---

### Post by lila on 2008-08-10
> **bpowell2005 said:**
> Try "sudo apt-get install ubuntu-desktop"

We tried, but it tells us something about locked files it can't open (I'm translating from French here).
...
ah! it works, but we had to add sudo!
It's installing, I'll get back in a few minutes!

---

### Post by lila on 2008-08-10
Ok, restarting...
loading ...
It Works!!!!!
Great!
Thanks a lot!

:guitar:

Lila

---

### Post by bpowell2005 on 2008-08-10
> **lila said:**
> Ok, restarting...
loading ...
It Works!!!!!
Great!
Thanks a lot!

:guitar:

Lila

Yes, I had to go back and add the "Sudo" when I saw it missing; didn't mean to add confusion!

Glad to hear you're back up and running! Well done!

---

