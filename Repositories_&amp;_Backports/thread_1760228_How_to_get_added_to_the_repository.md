---
title: "How to get added to the repository?"
date: 2011-05-16
forum: Repositories &amp; Backports
---

### Post by peyre on 2011-05-16
I'm not sure if this is the right place to ask this, but here goes.

I head up a small open-source project (a port of an old DOS game).  We did a .deb for the Linux version last release, but we're getting ready to declare it Stable and put out version 1.0.  So this seems like a good time to look into maybe making it easier for Ubuntu users to install it.  Does anyone know what would be involved in being added to the Ubuntu repository, or know where I can go to find out?

For reference, the project is at [http://sourceforge.net/projects/raceintospace/]("http://sourceforge.net/projects/raceintospace/").

---

### Post by kostkon on 2011-05-16
Wow really nice game!

You can apply for your application to appear in the software centre on the current release, without having to wait for the next version. The info is [here]("https://wiki.ubuntu.com/AppReviews").

Otherwise, you can just follow the standard procedures for adding your game to the debian/ubuntu repositories. More info [here]("https://wiki.ubuntu.com/UbuntuDevelopment/Uploading?action=show&redirect=DeveloperGuide%2FUploading").

Or you can just use a [PPA]("https://help.launchpad.net/Packaging/PPA").

Hope that helps.

---

### Post by peyre on 2011-05-16
Thanks!

Wow, so many options.  I'm afraid I'm a bit out of my element here.  I'm not a programmer, so this kind of thing is new to me.

There's nothing urgent to getting it into the repository (we're at least several weeks from release), so I might skip the first option.

So, is a PPA what Wine used to do for the cutting-edge release, where you had to manually add an APT line to Synaptic before it became available?  And do I understand this right that I may have to build a PPA in any case to get it into the repository?

---

### Post by donato roque on 2011-05-17
The PPA is very convenient yes.
You might check out the info about the software center. Nice game too.
The software center, i understand, can also show non-free games.

---

### Post by peyre on 2011-05-17
Thanks donato.  I've created a Launchpad account for it.  Looks like the next step is to sign our .deb with a GPG key...so I guess I'm on hold until we've prepared one (i.e, we're ready for the next release).  

Luckily I'm not trying to make it in time for an Ubuntu release that's almost here!

---

