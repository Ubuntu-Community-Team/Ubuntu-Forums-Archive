---
title: "marillat repository"
date: 2005-01-29
forum: Repositories &amp; Backports
---

### Post by DougInKY on 2005-01-29
I have been trying to add marillat as a repository on a reinstall of Ubuntu. I get told by synaptic now that marillat is trying to access a directory or a file that doesn't exist on the server. Here is the marillat line from my /etc/apt/sources.list:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

Anyone have any idea if something has changed on the marillat servers or if I have somehow screwed up my sources.list?

Doug

---

### Post by az on 2005-01-29
Did you do a reload (apt-get update)?

Marillat is an unofficial repository, so sometimes, the changing of packages is not as smooth as a stable repository.  I would suggest you try again at a later time...

---

### Post by DougInKY on 2005-01-29
Thank you azz for the fast answer. I will give it a wait as you said and see what happens.

Doug

---

### Post by DougInKY on 2005-01-29
You fix worked just fine. I just got access to the marillat repository. All I needed to do was give it a little time and it resolved itself. I guess they were updating the thing.

Doug

---

