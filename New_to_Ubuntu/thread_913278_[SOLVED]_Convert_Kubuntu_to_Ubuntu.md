---
title: "[SOLVED] Convert Kubuntu to Ubuntu"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by 44tr on 2008-09-07
I installed Kubuntu 8.04.1 KDE4 from a disk image.  I have now decided that Ubuntu suits my needs and style a little better.  I get the impression that it is possible to just convert from one to the other instead of doing a fresh install, but don't know how.  I want the result to be the same as having a fresh install of Ubuntu 8.04.1 (or whatever is latest) from the official disk image.

I looked at Adept and even selected Gnome-desktop-environment package for install, but it said "BREAK Install" in red which didn't seem to be a good sign.  Advice??

---

### Post by schauerlich on 2008-09-07
Follow this tutorial to install ubuntu-desktop (GNOME): [http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)
Follow this tutorial to remove kubuntu-desktop(KDE): [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Psychocats is useful. :)

---

### Post by 44tr on 2008-09-07
> **EDavidBurg said:**
> Follow this tutorial to install ubuntu-desktop (GNOME): [http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)
Follow this tutorial to remove kubuntu-desktop(KDE): [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Psychocats is useful. :)

Yes, I have been reading that site and have looked at those tutorials.  I wasn't completely sure I could use aptitude to remove Kubuntu desktop since I didn't use that to install or use the other method.  Install Ubuntu desktop with aptitude and remove Kubuntu with apt-get command listed?  Thanks for reply.

---

### Post by schauerlich on 2008-09-07
> **44tr said:**
> Install Ubuntu desktop with aptitude and remove Kubuntu with apt-get command listed?  Thanks for reply.

Yes, that should work.

---

### Post by napalm brain on 2008-09-07
I believe the cause is a bad dependency. You should be able to remove the dependencies, on doing that it should install from Adept.

---

### Post by DGortze380 on 2008-09-07
```

sudo aptitude install ubuntu-desktop

```

log out
choose session, gnome
log in

```

sudo aptitude remove kubuntu-desktop

```

---

### Post by 44tr on 2008-09-07
Thanks for the replies.  I followed the first advice above and it seems to have worked.  There may be some minor issues to work out (do I still have an Kubuntu bootup splash screen I wonder?), but I am where I want to be as far as I can tell.  Happy days :cool:

---

