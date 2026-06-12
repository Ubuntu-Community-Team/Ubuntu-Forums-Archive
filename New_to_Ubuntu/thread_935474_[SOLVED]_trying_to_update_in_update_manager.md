---
title: "[SOLVED] trying to update in update manager"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by fignig on 2008-10-01
but this error keeps popping up...

E: /var/cache/apt/archives/vlc_0.9.3+x264snapshot20080929+faad2.6.1-1~ppa1_amd64.deb: trying to overwrite `/usr/lib/vlc/demux/libavformat_plugin.so', which is also in package vlc-nox


is there something i need to add to repositories or what? i'm not sure what it means anyways, can anyone help?

---

### Post by Nano Geek on 2008-10-02
Usually deleting that file fixes the problem. I've done it before, and it hasn't caused any problems so far, but I'm not guaranteeing anything.

---

### Post by fignig on 2008-10-03
> **asjdfwejqrfjcvm msz34rq33 said:**
> Usually deleting that file fixes the problem. I've done it before, and it hasn't caused any problems so far, but I'm not guaranteeing anything.

lol so i should delete the file?

---

### Post by fignig on 2008-10-03
W: Failed to fetch [http://ppa.launchpad.net/c-korn/ubuntu/pool/main/w/wine/wine_1.1.5-1~ppa1_amd64.deb](http://ppa.launchpad.net/c-korn/ubuntu/pool/main/w/wine/wine_1.1.5-1~ppa1_amd64.deb)
  404 Not Found

is the error that is popping up now.

---

### Post by fignig on 2008-10-03
added wine to the repositories from the site with:
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list

and now i'm getting this error.
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263


wtf is happening?

---

### Post by Nano Geek on 2008-10-05
> **fignig said:**
> W: Failed to fetch [http://ppa.launchpad.net/c-korn/ubuntu/pool/main/w/wine/wine_1.1.5-1~ppa1_amd64.deb](http://ppa.launchpad.net/c-korn/ubuntu/pool/main/w/wine/wine_1.1.5-1~ppa1_amd64.deb)
  404 Not Found

is the error that is popping up now.There's probably a new version of wine available form that source and they deleted the old one. 

> **fignig said:**
> added wine to the repositories from the site with:
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list

and now i'm getting this error.
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263To verify repositories, Ubuntu uses keys that you can enter. This is supposed to keep people from adding repositories that you don't know about. However, this doesn't do anything. Unless you just can't stand the error message, I would just ignore it.

---

