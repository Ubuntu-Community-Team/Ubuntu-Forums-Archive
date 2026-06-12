---
title: "Using aget in apt-get"
date: 2006-03-28
forum: Repositories &amp; Backports
---

### Post by gtdj on 2006-03-28
Can I change apt-get inside downloader to aget ?
My APT mirror seems so slow.

---

### Post by aysiu on 2006-03-28
What's *aget*?

Can't you just change your mirror?

---

### Post by gtdj on 2006-04-07
[QUOTE=aysiu]What's *aget*?

Can't you just change your mirror?[/QUOTE]

In short, aget is wget that can use multi-thread downloading.

---

### Post by Aacron on 2010-04-03
I'd like to know how to do this myself... wget is all good, but it can get slow on my connection.  I'd like to get aptitude to use aget as it would reduce the times that I spend downloading updates.  wget generally manages to pull only 3Kb/s for some reason, though I have no problems downloading using aget.

---

### Post by Chessman on 2010-04-26
> **gtdj said:**
> In short, aget is wget that can use multi-thread downloading.

Check out [apt-fast]("http://www.mattparnell.com/projects/apt-fast-and-axel-roughly-26x-faster-apt-get-installations-and-upgrades.html"). The author uses axel, and it really speeds apt-get up.

---

