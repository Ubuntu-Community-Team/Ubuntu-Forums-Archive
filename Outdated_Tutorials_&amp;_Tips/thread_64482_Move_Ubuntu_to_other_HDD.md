---
title: "Move Ubuntu to other HDD"
date: 2005-09-11
forum: Outdated Tutorials &amp; Tips
---

### Post by gmalac on 2005-09-11
Hello,

I installed Ubuntu on my 2d drive (5GB) as I had WinXP in the first (20GB). After some months I only use Ubuntu but I am getting worried about the space (1 GB left).
I don't mind about WinXP so I could delete it. But I confess being at my 3d installation of Ubuntu, things work fine by now, so I don't want to go through this again.
Is there a way to somehow "move" Ubuntu, or at least part of it (like the home directory) to the primary disk?
Thanks !

Guy

---

### Post by lol on 2005-09-11
of course it's possible!

basically, all you have to do to move your linux on another drive is to copy all the files from one partition to the other (do it as root).

You then have to edit your /etc/fstab (the one on the new partition of course!) and boot loader config file to reflect the changes, then reboot :)

You can also setup your bootloader to boot both the "new" and the old linux, in case you have some troubles.

---

### Post by majikstreet on 2005-09-11
I just wanted to add that you really should read the announcements, as this is not the forum to ask questions :)


majikstreet

---

### Post by gmalac on 2005-09-12
[QUOTE=majikstreet]I just wanted to add that you really should read the announcements, as this is not the forum to ask questions :)


majikstreet[/QUOTE]

Ooops! very sorry I did not see that!

Guy

---

