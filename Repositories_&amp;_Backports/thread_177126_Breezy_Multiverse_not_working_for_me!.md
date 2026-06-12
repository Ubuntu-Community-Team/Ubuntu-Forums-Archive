---
title: "Breezy Multiverse not working for me!"
date: 2006-05-15
forum: Repositories &amp; Backports
---

### Post by TaterThePenguin on 2006-05-15
I'm a new Ubuntu Breezy Badger user. I've added the repositories in the exact way that the startup guide said, but for some reason, the Multiverse is nowhere to be found. I can download packages from the universe without problems; where has the multiverse disappeared to?

---

### Post by aysiu on 2006-05-15
[QUOTE=TaterThePenguin]I'm a new Ubuntu Breezy Badger user. I've added the repositories in the exact way that the startup guide said[/QUOTE] Can you link to the startup guide you used?

---

### Post by TaterThePenguin on 2006-05-15
[http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse](http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse)

---

### Post by DJ Scribblinni on 2006-05-15
The only thing that I would be able to tell you is to make sure the following two lines are in the sources.list file.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

If that doesn't help anything, I'm not sure what to tell ya man.

How did both of you reply in the time it took me to type this?,,,

---

### Post by aysiu on 2006-05-15
That guide wants you to add the repositories through Synaptic.

Usually that should be fine, but maybe (for whatever odd reason) those changes aren't actually taking in your /etc/apt/sources.list

Paste this command into the terminal: ```
cat /etc/apt/sources.list
``` and see if you get any lines that look like the following: ```
deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
``` If not, this guide may help you: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

