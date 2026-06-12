---
title: "Initial PPA version number?"
date: 2009-01-18
forum: Packaging and Compiling Programs
---

### Post by marmuta on 2009-01-18
Hi,
I'm trying to create a PPA for a little pet project of mine. Now I'm somewhat confused about the version string to use. I've looked through [PPAQuickStart]("https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPAQuickStart") and [PackagingGuide]("https://wiki.ubuntu.com/PackagingGuide") but I'm still not quite sure which it should be.
For a new package that is neither in Debian nor in Ubuntu, what would be the version?

myapp_0.1
myapp_0.1-0ubuntu1
myapp_0.1~ppa1
myapp_0.1-0ubuntu1~ppa1

I guess what I'm looking for is an easy to read table that covers all possible cases.

---

### Post by chrisccoulson on 2009-01-18
Perhaps you could start by taking a look [here]("http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Version"), which explains the Debian policy for version numbers

---

### Post by marmuta on 2009-01-19
Thank you, that helped clearing some up other questions I had. I'm still unsure about the ubuntu specific suffixes though. I guess I'll keep it simple and pick the myapp_x.y variant for now.

---

