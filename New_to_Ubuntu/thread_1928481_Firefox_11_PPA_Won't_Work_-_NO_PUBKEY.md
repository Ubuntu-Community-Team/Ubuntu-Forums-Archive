---
title: "Firefox 11 PPA Won't Work - NO_PUBKEY"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by Lucradia on 2012-02-20
Using the firefox-next ppa: [https://launchpad.net/~mozillateam/+archive/firefox-next](https://launchpad.net/~mozillateam/+archive/firefox-next)

Doesn't work, the GPG can't be used, and errors with NO_PUBKEY after you add the repo **ppa:mozillateam/firefox-next**

Any way to import the GPG?

---

### Post by yetiman64 on 2012-02-20
In a terminal use,
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CE49EC21
```Should add the key for you for that ppa.

---

### Post by Lucradia on 2012-02-20
That solved it, thanks.

---

