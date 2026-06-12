---
title: "BackUp/Synch tool"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by lscaglio on 2008-10-03
Hello everyone, I'm a real beginner and I need a little help.
I need an'app to synchronize the laptop with the pendrive, there is an'app like that (on window I use CotyToSynchronize)


Thanks a lot

Luca

---

### Post by swisscow on 2008-10-03
Try Unison, it's in Synaptic. Get the one with the front-end.

If you have any problems with permissions show the hidden files in your home folder, open up the .unison folder and with a text editor edit the profile you are using.

Add the line

perms=0

which basically then ignores permissions.

It takes a little thinking about, and it's worth trying some sample files before going live so to speak, but it's actually easy to use and very good.

---

### Post by bhadotia on 2008-10-03
I use Grsync to synchronize backup my backups.
Take a look at [this]("http://theaddicted.wordpress.com/2008/05/12/how-to-backup-ubuntu/").

---

