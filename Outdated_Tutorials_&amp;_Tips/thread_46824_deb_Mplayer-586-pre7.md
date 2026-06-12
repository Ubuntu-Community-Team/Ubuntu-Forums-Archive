---
title: "deb: Mplayer-586-pre7"
date: 2005-07-06
forum: Outdated Tutorials &amp; Tips
---

### Post by notos on 2005-07-06
i ve created a deb (yes my first one :-P) it haves gmplayer mplayer and mencoder i ve instaled it on my system and no problems so far :P y unpacked the original pre6 from the repos to make it as compatible as posible

download it from here

[http://xstudio.sourceforge.net/ubuntu/](http://xstudio.sourceforge.net/ubuntu/)

---

### Post by absinthe on 2005-07-06
I get an error when I try to install this.

sudo dpkg -i mplayer-586-1.0-pre7.deb
(Reading database ... 107027 files and directories currently installed.)
Unpacking mplayer-586 (from mplayer-586-1.0-pre7.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing mplayer-586-1.0-pre7.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/local/bin/mplayer')
Errors were encountered while processing:
 mplayer-586-1.0-pre7.deb

---

### Post by notos on 2005-07-07
My bad my bad the archive was corrupt. sorry now i cheked the MD5-Sums so it now wouldwork :P

Sorry

Download it again please :)

---

### Post by Breezy on 2005-07-07
Any chance create k7 or i386 packages ?
Thanks

---

### Post by tristan on 2005-07-13
Hmmm, I just tried to download and install mplayer-586-1.0-pre7.deb and got a similar message

```
Selecting previously deselected package mplayer-586.
(Reading database ... 88499 files and directories currently installed.)
Unpacking mplayer-586 (from mplayer-586-1.0-pre7.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing mplayer-586-1.0-pre7.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/local/bin/mencoder')
Errors were encountered while processing:
 mplayer-586-1.0-pre7.deb
```

Any suggestions notos?

---

