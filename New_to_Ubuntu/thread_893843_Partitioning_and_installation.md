---
title: "Partitioning and installation"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by David1000 on 2008-08-18
Is there a way of partitioning the hard disc so that when one reinstalls Ubuntu, one's programmes are not over-written; eg the latest FireFox being replaced with one that came out six months ago?

I believe all user progammes go on /usr so one can set this up as a separate partition.  But on reinstallation, these programmes will still be overwritten although programmes one has downloaded oneself will be left.  This does not appear to achieve the objective.

---

### Post by halitech on 2008-08-18
the only thing you can save in the way you are talking is the config files as they are in your home folder (as far as I understand) but making a seperate hope folder will at least save your settings so when you reinstall,  you'll have all your settings for when you install the programs.

(I hope some one can prove me wrong on this)

---

### Post by ggaaron on 2008-08-19
Installed programs go into may places /lib /usr and while it is possible to collect all files owned by firefox (in synaptic you can get info about installed package and there is a tab that says what files where installed by package) on reinstall you should remove all old firefox's files, put the saved ones and somehow trick apt to think that it has the newer version installed (probably edit it's cache) - all this in few words - not worth it. Deb files that you use to install packages are indeed packed files that you would collect if you'd copy all files owned by a package somewhere else, so in fact deb already provides you with a backed up higher version sometimes also giving scripts to make necessary changes during update. You can save the deb files so you don't have to download them again after reinstall.

---

