---
title: "songbird"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by reinnier on 2008-07-03
how do you install it?

---

### Post by bluepowder7 on 2008-07-03
[http://getsongbird.com/](http://getsongbird.com/)

looks like their web-page auto detects and gives you the install button


edit - oh wait, that's a tarball.  save it, extract it, and there should be a readme or install file.

---

### Post by reinnier on 2008-07-03
nevermind

found it on getdeb.net

[http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

---

### Post by ChameleonDave on 2008-07-03
It is available in the Linux Mint repositories.  I advise you to add the following line to your */etc/apt/sources.lis*t file:

```
deb http://packages.linuxmint.com elyssa main upstream import
```

You can then install Songbird via Synaptic or via the following command:

```
sudo apt-get update && sudo apt-get install songbird
```

---

