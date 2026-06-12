---
title: "apt-get connection timeout"
date: 2005-03-09
forum: Repositories &amp; Backports
---

### Post by barneyl on 2005-03-09
hi all,

just installed ubuntu, and the apt-get update had lots of connection timed out errors.

we have a pretty steady connection here, so i wondered if this is a common occurrence, and should i keep running the apt-get update until i get everything through?

many thanks,

-b

---

### Post by dorris on 2005-03-11
[QUOTE=barneyl]hi all,

just installed ubuntu, and the apt-get update had lots of connection timed out errors.

we have a pretty steady connection here, so i wondered if this is a common occurrence, and should i keep running the apt-get update until i get everything through?

many thanks,

-b[/QUOTE]
 not sure if this is the same prob as yours, but I've found that I often get corrupt partial downloads, so those files never download right again, clearing my partial apt folder often helps.
/var/cache/apt/archive/partial

---

### Post by jrave on 2010-11-12
Am also having this problem. Ubuntu 10.10 32 bit worked fine, but 64 bit gives timed out errors when doing apt-get update.

Edit: Not sure how this fixed. Right after posting this message I checked and found that UFW was disabled. I enabled it, and then updated my video driver with jockey (this is a fresh install). Restarted and had no more connection issues with apt-get.

---

