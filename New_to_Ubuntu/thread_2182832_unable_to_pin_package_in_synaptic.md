---
title: "unable to pin package in synaptic"
date: 2013-10-22
forum: New to Ubuntu
---

### Post by monkeybrain20122 on 2013-10-22
I had a package that I want to lock version in synaptic, I have pinned it and it is shown as such, but when I did mark all upgrades and upgrade in synaptic the package got upgraded anyway. 
This happens in Ubunu13.04.

---

### Post by ajgreeny on 2013-10-22
This is a new one!
What package?

---

### Post by monkeybrain20122 on 2013-10-22
bino. I compiled it myself from git. I could have made the version higher and it is not different from the repo version, so it is no big deal as far as this one package is concerned. But since it may not be package specific it would be quite disturbing if it is a general bug, I am posting this thread just want to find out if people experience it with other packages before I file a bug.

---

### Post by ajgreeny on 2013-10-22
Sorry, no idea about this.  Wait until another package is about to be upgraded but rather than carry out the upgrade pin it and see if it stops it doing so.

You could also try pinning the package by adding these lines to  /etc/apt/preferences:
```
Package: name
Pin: version (number from repos)
Pin-Priority: 1001
```

PS:  I'm not sure what the last line does but it certainly works on my system (or did work when I last tried it in 10.04 Lucid)

---

### Post by mc4man on 2013-10-22
> **monkeybrain20122 said:**
> bino. I compiled it myself from git. I could have made the version higher and it is not different from the repo version, so it is no big deal as far as this one package is concerned. But since it may not be package specific it would be quite disturbing if it is a general bug, I am posting this thread just want to find out if people experience it with other packages before I file a bug.
Pinning a package(s) in synaptic works here as far as it/they won't be upgraded from synaptic's "Mark all upgrades"

In your specific case if the pinned package was the same version & name as the repo package then it would be upgraded, that is to be expected

---

