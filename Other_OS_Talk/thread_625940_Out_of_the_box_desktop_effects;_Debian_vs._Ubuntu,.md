---
title: "Out of the box desktop effects; Debian vs. Ubuntu, Fedora, Suse..."
date: 2007-11-28
forum: Other OS Talk
---

### Post by Perpetual on 2007-11-28
Ok, this is a direct reflection of my inexperience with Linux and having to really deal with video card issues.  Question is, when I run Ubuntu Feisty/Gutsy, Fedora 8, Mandriva 2008, SuSE 10.3, PCLOS, Mint (maybe others I can't think of) I have desktop effects out of the box without doing anything with my video drivers.  When I installed Debian, I again did nothing with my video drivers and everything worked except after installing Compiz-Fusion I get an error "No compositing line" (verbage is from memory) and desktop effects are not possible.

Now, with that said, I did attempt at installing the ATI binary driver which did not work, crashed my xorg.  After more investigation I learned that my card is not supported (ATI Radeon Mobility 9200).

What I am trying to understand is why do the forementioned Distros work with Compiz but Debian does not?  looking at /etc/X11/xorg.conf, I really see no difference in the drivers section from one to the other.  Only noticeable difference were that some said driver 'radeon' while others said 'ati'.  None have a 'compositing' line.

So, what do I do to my Debian install to make it behave the same as Ubuntu?

Thanks guys!

Dell Latitude D600 Laptop
Pentium M Dothan, 1.6GHZ
512mb RAM
ATI Radeon Mobility 9200

---

### Post by b9anders on 2007-11-29
this might help

[http://wiki.compiz-fusion.org/Hardware/ATI](http://wiki.compiz-fusion.org/Hardware/ATI)

---

### Post by Perpetual on 2007-11-29
Thanks b9anders.  I will read into this tonight.

---

### Post by igknighted on 2007-11-29
When you install the binary ATI driver it overwrites the Mesa3d libraries, which the ATI binary does not use, but the open-source ATI driver does use (this is the driver that your are using to get desktop-effects to work).  I would un-install and re-install xorg via apt to get them back, or just reinstall the OS.

It might also depend which ATI drivers you used.  If you used the very latest that may not be the case, as I haven't used them in several months. But this used to be the case not too long ago.

---

