---
title: "VLC problems"
date: 2011-09-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by alphacrucis2 on 2011-09-27
Anyone noticed problems running VLC. Seems to be causing compiz to crash for me.


Edit:

I had earlier had a problem with pulseaudio not preserving volume settings after upgrade to Oneiric due to some sort of config compatibility problem. That was cured by deleting .pulse directory under my home directory. Well I thought I would try a similar thing with vlc. I found it stores some config settings under .config/vlc. Well removing that has fixed my problems. I'm marking this as solved as it may help someone else who hits this problems with this after upgrading from Natty.

---

### Post by Gnurfos on 2011-09-27
My VLC was completely freezing the system when I messed with its settings. But that was a few days ago. I did not re-try since then, because a freeze is not a pleasant experience.

---

### Post by komuta on 2011-09-28
I did the same thing, but it didn't completely solved the problem. Did you try to show the playlist window ? It makes VLC crash on my system.

A launchpad bug ([https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/854864](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/854864)) has been opened but no progress so far, thanks to apport failing to detect the crash.

---

### Post by mc4man on 2011-09-28
> **komuta said:**
> I did the same thing, but it didn't completely solved the problem. Did you try to show the playlist window ? It makes VLC crash on my system.

A launchpad bug ([https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/854864](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/854864)) has been opened but no progress so far, thanks to apport failing to detect the crash.
Likely related to this
[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/805303](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/805303)
You can workaround in several ways or wait till the latest idea for a fix is released

---

### Post by jj1two3 on 2011-09-28
I am having the same problem with VLC. It crashes every time I try to use it. :(

---

