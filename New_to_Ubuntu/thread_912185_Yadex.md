---
title: "Yadex"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by BarfBag on 2008-09-06
[http://www.teaser.fr/~amajorel/yadex/](http://www.teaser.fr/~amajorel/yadex/)

I stumbled across this neat little package this morning.  I tried to complile it, but was unsuccessful.  Could somebody tell me how?  Are there any .debs available?

Thanks!

---

### Post by scragar on 2008-09-06
Yadex used to be in the debian repo's, but it's now considered orphaned(so no=one is maintaining it anymore and it got removed for that reason :()

I'll see if I can build one for you on a virtualbox.

---

### Post by scragar on 2008-09-06
I built if from alien if your intrested(I couldn't get dpkg-buildpackage working, go figure).
```
wget ftp://rpmfind.net/linux/fedora/releases/9/Everything/i386/os/Packages/yadex-1.7.0-10.fc9.i386.rpm
sudo apt-get install alien
sudo alien -k yadex-1.7.0-10.fc9.i386.rpm

```
You'll still need iwad though.

---

