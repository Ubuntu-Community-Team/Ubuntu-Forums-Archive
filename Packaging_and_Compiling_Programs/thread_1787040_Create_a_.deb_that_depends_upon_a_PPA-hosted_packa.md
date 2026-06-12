---
title: "Create a .deb that depends upon a PPA-hosted package?"
date: 2011-06-20
forum: Packaging and Compiling Programs
---

### Post by DangerOnTheRanger on 2011-06-20
I have a game development kit that I'd like to package into a .deb. But, the underlying game engine that my GDK uses isn't in the package repos, it (that game engine's .deb package) is hosted on a Launchpad PPA.

Does anyone know how I'd list a PPA-hosted .deb as a dependency from a "normal" .deb package? Thanks!

---

### Post by MadCow108 on 2011-06-22
on the top right of your ppais a "edit ppa dependencies" link where you can set other ppas as dependencies for the current.

---

### Post by DangerOnTheRanger on 2011-06-22
Would your solution work if my .deb package was included in the official Ubuntu package repositories?

---

### Post by MadCow108 on 2011-06-22
it won't get included in the official archive if it has dependencies on a ppa.
first get the stuff in the ppa into the archive and then your stuff.

---

### Post by DangerOnTheRanger on 2011-06-22
Thanks, you just cleared practically everything up :)

So, I have to get my PPA-hosted dependency into the official package repositories, *then* get my .deb package into the official package repos? Sounds like hard work, but I'm willing to do it!

Thanks again!

---

