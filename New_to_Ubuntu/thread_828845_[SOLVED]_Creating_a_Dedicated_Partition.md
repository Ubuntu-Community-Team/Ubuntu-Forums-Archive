---
title: "[SOLVED] Creating a Dedicated Partition"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by LMD1990 on 2008-06-14
Hey guys, I've just gotten Linux Xubuntu, and I must say I am rather impressed with it. Currently I have it installed via Wubi, so it does not have it's own partition, but exists as a folder named "ubuntu" within my Windows XP-dominated hard disk. The current installation is 30GB.

However, after using Xubuntu for quite a while now and thoroughly liking it, I would like to give Xubuntu a dedicated partition. The dilemma I face is that I don't want to have to set it up all over again. In particular, the internet was a pain in the *** to install, since I had to go through the trouble of dragging my physical PC downstairs and hooking it up to the LAN, and then downloading wireless drivers etc. before I could get the thing to recognise my rather obscure wireless dongle.

In essence, what I am asking is if there is anyway I can give Linux Xubuntu it's own partition on my hard disk without losing ANY of the settings I have currently applied. (I have a 250GB hard disk, so I'd like to have it half XP and half Xubuntu.) I would like it to be a dedicated partition while remaining the same way I am using it now. It took so long to set up!

Can anyone help me out?

All help is appreciated :D

---

### Post by ajmorris on 2008-06-14
hi there,
i may be wrong... but as far as i know, unfortunately, you are going to have to install from scratch to migrate away from Wubi, and then set up your settings again :(
Any settings that are user specific, (i.e. are stored in /home/<user>), can be kept, but system wide settings can not.

AJ

---

### Post by Colin82 on 2008-06-14
According to Wikipedia you can do this, although I've never done it.
"While Wubi does not install Ubuntu directly to its own partition (which the developers consider a feature) this can also be accomplished by using LVPM, the Loopmounted Virtual Partition Manager, to transfer the Wubi-generated Ubuntu installation to a dedicated real partition, including a bootable USB keydrive."
[http://en.wikipedia.org/wiki/Wubi_(Ubuntu](http://en.wikipedia.org/wiki/Wubi_(Ubuntu))

Also, I think the Wubi website has some more info about it, but I can't access the site right now.
[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

Some research on those topics might lead you in the right direction.

---

### Post by ajmorris on 2008-06-14
> **Colin82 said:**
> According to Wikipedia you can do this, although I've never done it.
"While Wubi does not install Ubuntu directly to its own partition (which the developers consider a feature) this can also be accomplished by using LVPM, the Loopmounted Virtual Partition Manager, to transfer the Wubi-generated Ubuntu installation to a dedicated real partition, including a bootable USB keydrive."
[http://en.wikipedia.org/wiki/Wubi_(Ubuntu]("http://en.wikipedia.org/wiki/Wubi_%28Ubuntu"))

Also, I think the Wubi website has some more info about it, but I can't access the site right now.
[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

Some research on those topics might lead you in the right direction.

oooh, that is nice, i wasnt aware of this.

---

### Post by LMD1990 on 2008-06-14
> **Colin82 said:**
> According to Wikipedia you can do this, although I've never done it.
"While Wubi does not install Ubuntu directly to its own partition (which the developers consider a feature) this can also be accomplished by using LVPM, the Loopmounted Virtual Partition Manager, to transfer the Wubi-generated Ubuntu installation to a dedicated real partition, including a bootable USB keydrive."
[http://en.wikipedia.org/wiki/Wubi_(Ubuntu](http://en.wikipedia.org/wiki/Wubi_(Ubuntu))

Also, I think the Wubi website has some more info about it, but I can't access the site right now.
[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

Some research on those topics might lead you in the right direction.

Well I did my research and followed all of the above, and I am now rocking a seperate partition for Xubuntu. Thanks ever so much for all the help guys :D

---

