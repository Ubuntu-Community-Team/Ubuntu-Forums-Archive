---
title: "How to install Netbeans/Eclipse for all users?"
date: 2008-09-09
forum: Programming Talk
---

### Post by noctivago on 2008-09-09
Hi!

I'm trying to install the last versions of Netbeans and Eclipse from the original packages downloaded from their websites. The current version avaliable for Ubuntu Linux through Synaptic is older. My doubt is: It's possible to install the original packages for all users? How I can do this?

Thanks in advance.

---

### Post by CptPicard on 2008-09-09
Yes, it's easy. I usually install both of them as root under /opt, because both have rather extensive own directory systems and it's easy just to delete the old version by removing the directory.

For netbeans you run the installer as root and just point it at /opt, with Eclipse you just uncompress the tarball as root into that same place...

---

### Post by noctivago on 2008-09-10
Thanks CptPicard! Your hint worked fine :D

---

