---
title: "Where can I find 3rd-party repositories?"
date: 2012-01-01
forum: New to Ubuntu
---

### Post by xlucidreamx on 2012-01-01
I'm running 8.10 and I need a mirror of the standard ubuntu repository. 
I would change the line via software sources, correct?

So where would I look for a mirror of the ubuntu packages?

Sorry but I'm a noob. :(

Thanks for the help.

---

### Post by xlucidreamx on 2012-01-01
[Found it.]("https://launchpad.net/ubuntu/+archivemirrors")

---

### Post by coffeecat on 2012-01-01
> **xlucidreamx said:**
> [Found it.]("https://launchpad.net/ubuntu/+archivemirrors")

I very much doubt whether any of those mirrors will have packages for Ubuntu 8.10 which went end-of-life in April 2010. If you really want 8.10 packages, then you need to adjust your sources.list file for the old-releases repository. See here:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Don't try to upgrade from 8.10 from the instructions in that page, because 9.04 and 9.10 are also end-of-life and you are unlikely to be able to do it. And, be aware that any updates for 8.10 are nearly two years old now. There have been no bugfixes or security patches in that time.

Is there any reason you are running 8.10? You need to think about running a supported version of Ubuntu.

---

### Post by xlucidreamx on 2012-01-01
Yeah I figured that out. I did find "oldreleases .ubuntu.com" so it's taken care of.

I'm running 8.10 because my internet speed is too slow to upgrade.

Thanks :)

---

