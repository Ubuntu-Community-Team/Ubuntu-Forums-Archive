---
title: "Any incremental backup software for Ubuntu 12.04"
date: 2013-11-27
forum: New to Ubuntu
---

### Post by grandrigo on 2013-11-27
I've seen rsnapshot and duplicity but I dont know if there is another better/latest software? Any suggestions?

---

### Post by DuckHook on 2013-11-27
My suggestion has nothing to do with "latest", but is a case of older being better. Most of the powerusers I know use the tried-and-true *rsync* (graphical version is *grsync*) if the objective is an incrementally synced mirror over a NAS or external drive. For straight incremental backups, I just use *Déjà Dup*, which is a graphical wrapper for... what else?... *rsync*. It just takes away many of the inappropriate options and assumes appropriate ones so the user gets a clean and uncluttered interface, but what you are basically doing is using *rsync*. It is the default backup software for Ubuntu 12.04 and you don't have to download anything. A good primer for *Déjà Dup* is [here]("http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/").

---

### Post by Paulgirardin on 2013-11-27
I use Back in Time ,I prefer it to Deja Dup. Get it in the software center

---

### Post by bashiergui on 2013-11-27
Deja Dup ships with Ubuntu and makes it easy to back up to UbuntuOne
[http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/](http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/)

---

### Post by grandrigo on 2013-12-09
I am thinking about using rsnapshot. My idea is to backup two linux machines in a third box using rsnapshot and probably tweak to work with rsync. Any suggestions?

---

### Post by Dave_L on 2013-12-09
I use rsnapshot to backup one machine to an external drive. As you may know, rsnapshot is simply a Perl script that uses rsync.

rsnapshot includes documentation, including examples.

---

