---
title: "File Version Numbers"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by Polydorus on 2013-04-05
I've been experimenting with DVD::Rip.  The instructions mention that some additional files would be useful, xvid4conf for example.  Any version from v. 1.6 to 1.12 will do.  Synaptic can get me v. 1.12-0.1 which looks like it will do the trick.  However rar and mplayer files have file version numbers that I don't understand.  DVD::Rip wants any version of rar from 2.71 to 2.99 and mplayer from 0.9 to 1.0  Synaptic can get me rar 2:4.0.b3-1 with a similar result for mplayer.  What's the colon for?  Is this version 2.4 or 4.0?

Thanks

---

### Post by Polydorus on 2013-04-06
Anyone? TIA

---

### Post by sandyd on 2013-04-06
> **Polydorus said:**
> I've been experimenting with DVD::Rip.  The instructions mention that some additional files would be useful, xvid4conf for example.  Any version from v. 1.6 to 1.12 will do.  Synaptic can get me v. 1.12-0.1 which looks like it will do the trick.  However rar and mplayer files have file version numbers that I don't understand.  DVD::Rip wants any version of rar from 2.71 to 2.99 and mplayer from 0.9 to 1.0  Synaptic can get me rar 2:4.0.b3-1 with a similar result for mplayer.  What's the colon for?  Is this version 2.4 or 4.0?

Thanks

ignore the 2:. its [4.0]("http://packages.ubuntu.com/precise/rar")

Technically, if you install dvd::rip from the repos, it is compiled against the library versions that are avaliable in the repository anyways, so you don't even really need to check to see if it will work or not. If it doesn't work, it should be a bug.

---

### Post by schragge on 2013-04-06
In case you are curious, the **2:** thing is called [epoch]("http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Version") in Debian parlance. It helps e.g. when upstream version numbering scheme changes in an incompatible way:
```
20120315-beta -> 1.0
```
To ensure smooth upgrades, Debian makes this look like:
```
20120315-beta -> 1:1.0
``` as anything after 1: compares greater than bare 20120315 (0: is implied before it).

There are other uses for it, too.

---

### Post by Polydorus on 2013-04-07
> **sandyd said:**
> ignore the 2:. its [4.0]("http://packages.ubuntu.com/precise/rar")

Technically, if you install dvd::rip from the repos, it is compiled against the library versions that are avaliable in the repository anyways, so you don't even really need to check to see if it will work or not. If it doesn't work, it should be a bug.

Thanks sandyd.  I was going ahead and download whatever was available but got to wondering what the version numbers meant.

---

### Post by Polydorus on 2013-04-07
> **schragge said:**
> In case you are curious, the **2:** thing is called [epoch]("http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Version") in Debian parlance. It helps e.g. when upstream version numbering scheme changes in an incompatible way:
```
20120315-beta -> 1.0
```
To ensure smooth upgrades, Debian makes this look like:
```
20120315-beta -> 1:1.0
``` as anything after 1: compares greater than bare 20120315 (0: is implied before it).

There are other uses for it, too.


Thanks for the explanation** schragge.**[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1783515")

---

