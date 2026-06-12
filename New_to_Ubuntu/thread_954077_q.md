---
title: "q?"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by &#1575;&#1604;&#1593;&#1585;&#1576;&#1610; on 2008-10-20
hi
how i can run program with rpm extension in ubuntu and my distribution is ubuntu 8.04

---

### Post by Paqman on 2008-10-20
You can convert an .rpm to a .deb using alien.

[Alien HowTo](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html)

Once you've got a .deb, you can just click to install.

---

### Post by a0u on 2008-10-20
It is, however, preferred that you obtain a Deb version if possible.  Alien may not work perfectly.

---

### Post by Kosimo on 2008-10-20
> **&#1575 said:**
> hi
how i can run program with rpm extension in ubuntu and my distribution is ubuntu 8.04

Ubuntu is a Debian fork and uses another package called .deb
.rpm is a Red Hat *and variants like Fedora* package.

What package are you trying to install? It should be in the official repositories. 
If doesn't you can also try to convert from rpm to deb using a small program called alien. (open a terminal and type ```
sudo apt-get install alien 
```

There are tons of tutorials around there that will help you to convert that rpm to a deb. (Be careful it doens't works always)

But as I said, first, try to have a look if you can find that particular program in Synaptic. If doesn't, then try to find a .deb, or even better, compile by yourself.

---

### Post by bodhi.zazen on 2008-10-20
Best to install from the Ubuntu repositories (they are quite large) or from source.

Use alien as a last resort as it can cause breakage.

---

