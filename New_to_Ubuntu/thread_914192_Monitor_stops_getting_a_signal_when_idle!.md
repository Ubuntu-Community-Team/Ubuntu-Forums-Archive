---
title: "Monitor stops getting a signal when idle!"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by dagoss on 2008-09-08
If I leave my computer and come back, when I turn my monitor back on, it claims that it isn't getting a signal.  The only thing I can seem to do is ctrl+alt+bkspc to restart the X-server.  I found a similar [ bug here]("https://bugs.kde.org/show_bug.cgi?id=170635").  I'm pretty sure that fglrx is the non-free Raedon driver, yes?  That's what I'm using right now (for a Raedon 9600 XT).

I think it might be a good idea to try removing the non-free driving and using something else to see if that is specifically causing the problem, but I'm not quite sure how to do that safely.

I'm using KDE 4.1

EDIT:  I think I need a package called "xserver-xorg-video-ati", then I need to sudo modprob -r fglrx to get rid of that and then add the raedon driver (is that what it's called?).  I think.  I checked /etc/modules and fglrx isn't there (but it is in lsmod), so I'm not sure when it's getting loaded.  Is that something the X-server itself handles?

---

### Post by dagoss on 2008-09-08
How about this:

I replace
```

Section "Module"
     Load "glx"
EndSection

```

with...

```

Load "raedon"

```

Will that do what I think it does if I restart the X-server?  I'd like to know if this is a driver problem or a problem with KDE4.  I never had this problem with Gnome, however I did start using a new monitor at the same time I started using KDE4.

EDIT:  Or maybe related to the fact that my new monitor uses DVI instead of VGA?

---

