---
title: "Problem with partially installing Hardy"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by hollandmc on 2008-05-03
So I tried to update to Hardy via update manager and my computer froze (last I saw it was at the "installing" phase). The screensaver wouldn't turn off, it was unresponsive no matter what I did, and even though I let it sit for hours and hours and hours, it refused to finish installing and reboot itself. I had to turn it off... Now it won't start up correctly and I think it's because it's stuck between my old version (7.10) and 8.04. I've tried to boot it three times, leaving time between the restarts: the first time it allowed to me log in and all that, but once it got to the screen with the mouse and brown background, it stopped. I  could move the mouse, but GNOME wouldn't start. The second time I didn't even get that far because I got an "out of frequency range" message on my monitor (although the login screen sound effect played through my speakers). The third time was the same as the first... 

My question is this: can I fix this without having to re-install 7.10? Like edit the boot menu or something? I have all my documents backed up, thankfully, so if I do have to re-install it would be that big of a deal, but I'd like to avoid having to install all my programs and codecs and changing all my preferences again if at all possible. 

Thanks in advance.

---

### Post by zvacet on 2008-05-04
Boot in recovery mode and type

```
dpkg --configure -a
```

or 

```
apt-get -f install
```

---

