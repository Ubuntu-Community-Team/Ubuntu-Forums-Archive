---
title: "Synaptic doesn't use /etc/apt/sources.list?"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by oxsyn on 2008-11-03
I assumed that synaptic = aptitude.  Apparently I'm wrong.  These are two different package managers?  

I added several lines manually, to the bottom of my /etc/apt/source.list file:

> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

But when I look at Administration -> Software Sources, I don't see any of these sources listed.

Does this mean that "sudo apt-get update" != Administration -> Update Manager?

---

### Post by Fass on 2008-11-03
Run "Reload" and checked under "Third party software" in Synaptics?

Anyway, aptitude is not synaptics. Apt-get update is not "update manager". They all do use /etc/apt/sources.list, though.

---

### Post by drs305 on 2008-11-03
As Fass said, some such as ppa.launchpad, will be under Third-Party. The addition of the -security repositories will check the 'security' tick box in the Updates tab, and intrepid-proposed will tick the 'pre-release proposed' tick box in updates. They are all there, they just aren't as obvious as sources.list.

---

### Post by oxsyn on 2008-11-03
Ah, thank you.  That clears it up.

---

