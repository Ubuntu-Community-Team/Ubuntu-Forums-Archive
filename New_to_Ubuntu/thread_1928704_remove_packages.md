---
title: "remove packages"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by leilton on 2012-02-20
Can someone advise as to whether are not it is OK to remove items in which  I have no interest in  my Lubuntu and Kubuntu systems.

I certainly do not need, or intend to use, Chrome and several of the other internet choices, and I prefer Clementine to all the others shown.

Will I be doing any damage if I remove them?



:confused:

---

### Post by snowpine on 2012-02-20
Probably no damage, but also no benefit (unless you are running very low on disk space).

When you remove a package, Software Center will list any other package(s) that will be removed in the process. **Read this list carefully** and don't say Yes unless you're absolutely certain you wish to proceed! :)

---

### Post by leilton on 2012-02-20
> **snowpine said:**
> Probably no damage, but also no benefit (unless you are running very low on disk space).

When you remove a package, Software Center will list any other package(s) that will be removed in the process. **Read this list carefully** and don't say Yes unless you're absolutely certain you wish to proceed! :)
thank you very much.   Point taken, will leave well only for now

---

### Post by tnicewicz on 2012-02-20
sudo apt-get remove <selected package>

---

### Post by Scott Baker on 2012-02-20
You state that you're looking at removing primarily internet based packages. These NORMALLY won't cause problems. On the other hand, say you were to remove a media player (VLC for example), you could have some files in this that also run Brasero. Removing one COULD adversely effect the other. (Some of us have learned these lessons the hard way) As others have already said, if you have a list that pops up stating that other stuff is going to be removed, be careful. It's very likely that some other package is using that item.  *** before anyone questions it, I used the media player issue strictly as an example***

---

### Post by Lisiano on 2012-02-20
Heads up as you will be wondering, if you try to remove a package and it tries to remove ubuntu-desktop, kubuntu-desktop, xubuntu-desktop or lubuntu-desktop, then they are okay to remove, those packages exist to ease upgrades to newer releases as they depend on everything (GUI-wise I think) that is included in the next release. So if you do remove one of those, be sure to reinstall it along with whatever it wants to install if you don't want headaches during a release upgrade. Either way, I see no reason in removing the default stuff unless you are 1) tight on space 2) have a bandwidth limit 3) sluggish internet connection.

---

