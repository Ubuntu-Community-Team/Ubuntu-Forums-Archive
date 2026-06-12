---
title: "how to remove gnome"
date: 2011-07-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by inportb on 2011-07-16
So like, last night's update installed GNOME and Metacity. Needless to say, I am slightly confused. It would have been fine if they stayed out of my way, but they have reconfigured the background of the window switcher. See:

[CENTER][[IMG]http://i55.tinypic.com/2hdtxsj.png[/IMG]]("http://i55.tinypic.com/2hdtxsj.png")[/CENTER]

It's somewhat distracting. Which packages should I get rid of? Thanks!

/edit:

[Done!](http://ubuntuforums.org/showpost.php?p=11053640&postcount=7)

---

### Post by Linux_junkie on 2011-07-16
That is not Gnome!

---

### Post by inportb on 2011-07-16
Well, the background (with the "screenshot.?" icon) is exactly what the desktop looks like when I select GNOME from the KDM window manager menu, so I concluded that *some* piece of GNOME got lost and found its way into the KDE interface. If that is not the case, what do you think it is?

It's definitely not a big problem because it only shows up in the window switcher, but I'd appreciate any help with this!

---

### Post by sgage on 2011-07-16
Linux_junkie is right - you've got something else going on there. Since you're running Kubuntu, an update isn't going to magically install gnome stuff anyway.

It seems like you inadvertently installed some sort of docking app or something. Not sure what to tell you, except maybe look in the update history to see if you can figure out what's happening...

[edit: I see you apparently installed gnome-shell at some point if "gnome" shows up in KDM. Still, it looks like you installed some sort of launcher thingie for KDE - it even has the little KDE "cashew" symbol on it.]

---

### Post by inportb on 2011-07-16
Thanks for the tips. I'm just going to list all the gnome-* packages I have installed and remove most of them. Are there any other globs that I should be looking at?

And yeah, that is indeed a launcher; it's what KDE automatically uses given a netbook-sized screen. I guess you could say the Kubuntu installer pulled it in with KDE, but it's really part of KDE.

/edit:

Aha! It looks like removing gnome-session-bin takes a whole boatload of packages out with it, and they look like what got installed last night. I'm still not sure what package I installed that resulted in this; oh well...

I might as well take Unity out with it too, since it also got installed.

---

### Post by sgage on 2011-07-16
> **inportb said:**
> Thanks for the tips. I'm just going to list all the gnome-* packages I have installed and remove most of them. Are there any other globs that I should be looking at?

And yeah, that is indeed a launcher; it's what KDE automatically uses given a netbook-sized screen. I guess you could say the Kubuntu installer pulled it in with KDE, but it's really part of KDE.

You could try just un-installing gnome-shell. That should leave you with a lot of auto-removable files that you can uninstall easily. I'm not sure what an installation of gnome-shell would have pulled in if you started with stock Kubuntu - probably a bunch of standard Gnome apps and such, along with the Gnome 3 stack.

It might take a little while, but you'll sort it out.

---

### Post by inportb on 2011-07-16
Yeah, that's what I ended up doing, but it didn't take much else with it. *gnome-session-bin* seemed to be the main dependency-generating package, though, so I autoremoved that and cleaned up :D

Problem solved! Thanks for the suggestions.

---

### Post by ranch hand on 2011-07-16
You could, for future folks looking through here, mark this thread solved.  It is under 'thread tools" top right of this page.

---

