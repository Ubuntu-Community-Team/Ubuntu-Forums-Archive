---
title: "how to replace local mirror to sources.list"
date: 2006-01-20
forum: Repositories &amp; Backports
---

### Post by Zelut on 2006-01-20
My ISP mirrors the ubuntu repos but I'm unsure how to update my sources.list to use their files instead.  Can someone give me some tips?

Here is a link to the http of the [local mirror]("http://mirrors.xmission.com/ubuntu/dists/")

Much appreciated.  I figure this'll give me quicker downloads & also they don't include "in-network" bandwidth on my limit.  Thanks

---

### Post by manicka on 2006-01-20
try

deb [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu) breezy universe main restricted multiverse

etc

back up your current sources list first

---

