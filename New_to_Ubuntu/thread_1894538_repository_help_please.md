---
title: "repository help please"
date: 2011-12-12
forum: New to Ubuntu
---

### Post by weephatz on 2011-12-12
Hi there, 

I know this has been posted a few times but I'm struggling to find a solution that works for me.

Getting red triangle warning saying -

 failed to download repository information. Detail:

"W:Failed to fetch [http://ppa.launchpad.net/goehle/goehle-ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/goehle/goehle-ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/goehle/goehle-ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/goehle/goehle-ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/goehle/goehle-ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/goehle/goehle-ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead."

I have seen a few suggestions on here, suggesting sudo apt-get update then upgrade - tried that, no errors thrown back at me but when I tried software update afterwards I get the same result I was getting before.

Another suggestion I've seen is to untick from the repository list, but I'm hesitant to do that because PPAs like "...ubuntu/dists/oneiric/main/source/Sources" strike me as important sources for updates (I could be completely wrong about this, I'm new to linux in general).

This all started after I ran suggested updates on the Update Manager this morning, which looked like they were updating kernel.
If required, I'm running: 11.10, Unity, 3.0.0-14-generic, x86_64

Any help would be greatly appreciated :)
Thanks in advance

---

### Post by RealityMaster on 2011-12-12
Go into your software sources (Software Center --> Edit --> Software Sources) and remove the sources that give you the 404.  Then visit the vendor and find the new ppa to add.  I had a lot of these after the upgrade to 11.10 from 11.04 as well.

---

### Post by RealityMaster on 2011-12-12
Also, some of them may be duplicate entries, one working and one not...

---

### Post by weephatz on 2011-12-12
Removed sources and added new ones, problem solved.
Thanks for the help and the quick reply :D

---

### Post by RealityMaster on 2011-12-12
:)

---

