---
title: "Backing Up What Else?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Patriot1776 on 2008-04-26
Okay, I let my system run all night basically tarring up my entire /home directory (28 gigs) onto my new 80 gig external hard drive.  I've also tarred up my /etc directory as well.  Is there anything else I need to tar up to where should I need to wipe and reinstall, I can get back to where I'm at exactly now?

---

### Post by frup on 2008-04-26
I would say making sure you have included all the hidden config file in home and not just the visible files. Possibly you might want to back up all your install .debs in /var/cache/apt/archives/ so you could have all the same packages again?

---

### Post by Patriot1776 on 2008-04-26
I'm pretty certain I got all the hidden ".xxx" stuff in the home directory because this was the exact command I ran in /home:

```
sudo tar -cjvf /media/disk/homebackup.tar.bz2 *
```

And while checking on it occasionally while doing other things, I did see it numerous times digging through all the various "user/.xxx" directories too, and running the command that way ensured the other two occasional users' stuff and configs, not just my own, were tarred up too.

And alright, I'll hookup and remount the external drive and stick the .debs from that directory you mentioned as well.  I've still got an ample amount of space on it (43 gigs left) to stick anything else.  The 28 or so gigs of my home directory was practically all the space currently used up on my internal disk.

---

