---
title: "KDE Apps under Gnome"
date: 2005-03-19
forum: Repositories &amp; Backports
---

### Post by audax321 on 2005-03-19
Hello,

I'm using hoary right now and would like to use some KDE apps under Gnome that I like better than the Gnome alternatives by installing as little of KDE as possible. If I install amaroK and korganizer from synaptic and it takes care of the dependencies for the packages, will they run under Gnome?

Thanks.   :-)

---

### Post by ember on 2005-03-19
Sure they will. Make sure to
a) have kcontrol to setup a nicer theme and fonts for KDE stuff
b) check your .ICEauthority file owner and permissions before you reboot, some KDE-Apps may accidentially reset them to root:root when you start them the first time (for me it was K3b that I ran in a root terminal - guess that's why it broke). Should be like:
-rw-------    1 uname    uname        1630 2005-03-19 10:26 .ICEauthority
where uname is replaced with your username. If it isn't, do a 
chown uname:uname .ICEauthority
where again uname is replaced with your actual username.

It should work that way.

---

