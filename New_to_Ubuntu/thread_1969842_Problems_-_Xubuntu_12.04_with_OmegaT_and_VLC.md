---
title: "Problems - Xubuntu 12.04 with OmegaT and VLC"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by Journeyman1962 on 2012-04-30
Hi,

Need some help. Had a huge search round, can't really find anything that sorts out the problems:

Have just installed Xubuntu 12.04 on the laptop in preparation for putting it on the desktop (production computer!)

Re: OmegaT

I'm a freelance translator and use OmegaT A LOT. 

I can't get the spellchecker to work despite locating the dictionaries (.aff and .dic) and changing the location directory in OmegaT accordingly (making sure the names are the same and all that, as suggested on the OmegaT forums, among other places).

When selecting some tabs on the options menu - the program hangs, to a degree that I have to reboot the computer.

The OmegaT interface does not respect the desktip theme (It did, automatically, with Gnome on Ubuntu 10.10) - this is a minor problem. 

Re: VLC

They seem to have sorted out the audio problems of 11.10. But now, the fullscreen option won't occupy the whole screen. If I click the icon in the player, my side panels remain visible, if I hit F11, the VLC top menu and window buttons at the bottom are still visible.

Any help from anyone who's manged to sort out any othe problems, gratfully received.
Thanks
Tim

---

### Post by pqwoerituytrueiwoq on 2012-04-30
i just used vlc a couple hrs ago full screen seemed normal to me, though i use the keyboard controls (f for fullscreen, space for pause)

---

### Post by Journeyman1962 on 2012-05-01
Tried f - still doesn't work. Main vlc menu (top) and grey control bar (?) are still present on screen.

Confused. Might it be a vlc preferences problem - have checked round, can't see anything wrong/odd/different from version on 11.10.

Tim

---

### Post by Irihapeti on 2012-05-01
Re OmegaT:

Which version of Java do you have installed, and which version is on your previous system?

I'm wondering if it has anything to do with Oracle Java no longer being in the repos.

---

### Post by Journeyman1962 on 2012-05-01
OK. How do I find that out?????

(This is the absolute beginner forum, after all...)

---

### Post by Irihapeti on 2012-05-01
For each installation, open a terminal and enter the command:
```

java -version
```

That gives a brief summary.

---

### Post by Journeyman1962 on 2012-05-01
Yes. It's JDK. But I've now downloaded the omegat version with JRE included and it's stable.

Thanks a lot.

Tim

---

### Post by Journeyman1962 on 2012-05-02
> **pqwoerituytrueiwoq said:**
> i just used vlc a couple hrs ago full screen seemed normal to me, though i use the keyboard controls (f for fullscreen, space for pause)


OK. Solved the vlc "problem"

Maybe it was something that everyone knew except me: :oops:

If vlc window is maximised (i.e. window top frame buttons - minimise, maximise, close), it won't go to fullscreen completely. Only works when window is not maximised.

Tim

---

