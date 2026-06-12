---
title: "PClinux &amp; Mandriva"
date: 2008-01-08
forum: Other OS Talk
---

### Post by swoll1980 on 2008-01-08
What's the difference. They seem to be the same to me the only difference I've seen is the synaptic package manage. They have been a separate distro for four years is this all they have to show for it?

---

### Post by igknighted on 2008-01-08
Mandriva: newer packages, commercial support and a more well rounded distribution (64 bit, PPC versions, server versions, etc.).

PCLOS: Simplified the install procedure with liveCD (had one long before Mandy), re-arranged menus and includes things like dvdcss2 that Mandy cannot by default.

And they really haven't been split for four years.  PCLOS re-based to Mandriva after Mandriva 2007 due to being unable to do some major upgrades themselves (rebuilding everything with a newer version of GCC IIRC), so really they have only been split for just over a year.

---

### Post by jrusso2 on 2008-01-09
Takes a bit more fishing around and adding a lot of repos in Mandriva 2008.  I had to add a lot of easy urpmi repos to find a lot of needed things.

---

### Post by igknighted on 2008-01-10
> **jrusso2 said:**
> Takes a bit more fishing around and adding a lot of repos in Mandriva 2008.  I had to add a lot of easy urpmi repos to find a lot of needed things.

Not true, "easy URPMI" is actually the hard way.  You can add nearly all these repo's through the GUI automatically, then the 4 PLF repo's (free and nonfree are all you really need, then free-backports and nonfree-backports for the very latest stuff) are all you need to add yourself (no different than adding medibuntu or others on Ubuntu).

When you start the package manager the first time, it will ask if you want to add distribution sources.  Click OK and add everything you need, you can change it through the Drak control panel later if need be.  I don't believe you can add PLF repos this way, but as mentioned above those are fairly simple, and easyurpmi can do it for you.

Oh, and if you want to add those EasyURPMI repos quicker... open a text file, paste the entire code easyUrpmi tells you, add this line in front of it "#! /bin/sh", and save it.  Then type 'sh <filename>' and it will do it all, no need to manually enter each line.

---

