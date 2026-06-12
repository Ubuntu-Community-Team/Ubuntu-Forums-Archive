---
title: "Configuration / application files missing after running out of space"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by djmac on 2012-03-05
Hi all,

My computer ran out of storage - and the free space got very very low - (thanks to a rogue dropbox account). I deleted about 50GB - restarted my computer (running horribly slow). The 50GB was *not* from my home directory - it was mainly document files and videos.

Now I seem to have lost a random selection of configuration and/or application files.

For example - when I opened my chromium browser - all themes and extensions history and book marks are gone. When I restarted skype, had to redo the EULA etc. 

Obviosly these are pretty minor problems - but there a few missing "things" that I would like back - or at least no where they went!

Cheers, and thanks in advance!

---

### Post by blazemore on 2012-03-06
It seems somehow you've accidentally deleted some config files from your home directory.

Config files are stored in "hidden" directories: those that start with a dot(.)

Example include .config, which contains, among other things, your Chromium profile.

---

