---
title: "AMD64 users: Possibly Broken ia32-libs After Today's Update 09-29-2011"
date: 2011-09-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by DeadSuperHero on 2011-09-30
Hey all,

Just wanted to give everyone a heads up on a strange problem I've encountered after updating today. I'm not totally sure what broke, and I'm not even really sure what to report as a bug due to the nature of this problem, but I'll do my best to let others know about it. If anyone else is experiencing this, then I'm clearly not the only one.

I was getting ready to play ZSNES (32-bit) today, but upon opening it, I got errors that the package was missing libraries for i386, even though ia32-libs is installed. This struck me as an odd but not totally uncommon problem, so I purged my zsnes package and attempted to install it again. The installation went without a hitch, but now I have this surreal problem:

Attempting to run ZSNES from either the command "zsnes", "/usr/bin/zsnes" or even any binary that happens to be zsnes comes up with the error: "/usr/bin/zsnes: No such file or directory", even though there's totally a binary there.

At first I thought that this problem was just with my zsnes package after the update, but now I'm having the exact same problems with Wine, showing similar errors.

Was there a package in an update that forced a regression?

---

### Post by QIII on 2011-09-30
Eh.  I'm using Oneiric. Still in development.  Have to expect the odd breakage still.

I just found out that several applications (Thunderbird, Firefox and more) do the old open/close immediately trick in KDE, but run fine in GNOME shell and Unity.

It'll all be sorted out tomorrow.  Right?

If not, I'll send a nasty-gram via Launchpad.

---

### Post by DeadSuperHero on 2011-09-30
Yeah, I know. It's just that the nature of this error kind of threw me. Figures, because I was really getting into Earthbound over the last few days. :(

---

### Post by QIII on 2011-09-30
Found a workaround for my problem.  Seems someone forgot to change a reference for a GTK2 library to a GTK3 library somewhere when the latest update dumped the older file.  Just downloaded a .deb with the old one and re-installed it.

The fun of development releases.

It's not like my clients ever call to say something I developed blew up on them when I sent an update!   :p

---

