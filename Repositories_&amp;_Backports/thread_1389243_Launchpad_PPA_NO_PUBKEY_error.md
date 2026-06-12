---
title: "Launchpad PPA NO_PUBKEY error"
date: 2010-01-24
forum: Repositories &amp; Backports
---

### Post by nabilalk on 2010-01-24
Lately I have been getting the following error when attempting sudo apt-get install or sudo apt-get update. I'm running Karmic.
```
Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
``` I got this error [(Pastebin)](http://crunchbanglinux.org/pastebin/470) when attempting sudo apt-get install build-essential and also during apt-get install thunderbird. I tried updating my software sources and [this error popped up](http://crunchbanglinux.org/pastebin/471). The issue appears to be a missing PUB_key?
```
GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5Failed to fetch http://mirrors.easynews.com/linux/ubuntu/dists/karmic/main/binary-i386/Packages.gz  403  Forbidden
```

I found [this post](http://www.stefanoforenza.com/solve-your-no_pubkey-ppas-in-a-snap-or-a-script/) and tested out the suggest script. No such luck. Hopefully someone on here will have an answer. In the mean time, I will keep looking. Thanks for the help.

---

