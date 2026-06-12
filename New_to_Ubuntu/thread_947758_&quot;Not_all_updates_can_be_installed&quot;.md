---
title: "&quot;Not all updates can be installed&quot;"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by damonjablons on 2008-10-14
Hey Forumers,

My Ubuntu installation is telling me that there are necessary updates that need to be installed, but when I run the Update Manager it gives me the following warning:

"""
Not all updates can be installed

Run a partial upgrade, to install as many updates as possible.

This can be caused by: ...
"""

When I attempt to run a partial upgrade I get the following error message:

"""
Error authenticating some packages

It was not possible to authenticate some packages.  This may be a transient network problem.  You may want to try again later.  See below for a list of unauthenticated packages.

bogofilter-common
brasero
gimp
gimp-data
gimp-python
gnome-do
libbabl-0.0-0
libgegl-0.0-0
libgimp2.0
libnotify0.4-cil
libpurple0
pidgin
pidgin-data
pidgin-facebookchat
tomboy
transmission-gtk
ubuntu-tweak
ultamatix
wine
wine-doors
"""

How do I remedy this situation and keep it from happening in the future?  I'm mostly curious about what caused this.

Thanks in advance.

-D

---

### Post by Victormd on 2008-10-14
You can accept the partial install, most likely it will require you to reboot after it's done, then run the upgrade again, or click on close, run the updates, it will most likely install something that requires you to restart, then finalize it.

This can happen because it will update your kernel and another package update is dependent on the new kernel (that's why you will need to reboot to install the remaining updates)... :)

This can have other causes but it's not something you should be worried about. You will see this more often, when installing a beta release because of the increased updates per day.

---

### Post by eolson on 2008-10-14
Happened to me too.   Took the partial and rebooted then ran the update again and everything was fine.   Need to expect weird things when your messing with a beta edition.

One reason I always use a spare machine for Alfa and Beta playing.

---

### Post by bobnutfield on 2008-10-14
It is usually NOT a good idea to do a partial upgrade, but as Victormd has said, it does become necessary sometimes with developemnt releases.  I have had to do two partial upgrades and it turned out OK.

---

### Post by Victormd on 2008-10-14
Yeah, I'm assuming that this is for Intrepid. If you're using Hardy, then don't do the partial update (at least not yet).
In this case, click on close (this will take you to the software update window) run the updates that are selected (don't select any thing other than what was automatically marked), it will most likely install something that requires you to restart. Reboot and run the update manager again.

---

